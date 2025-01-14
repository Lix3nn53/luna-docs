<script>
	import { Heading, P, A, Alert, Button, Hr, Li, List } from 'flowbite-svelte';

	import { CodeBlock } from 'svhighlight';
	import 'highlight.js/styles/base16/papercolor-dark.css';

	import {
		Table,
		TableBody,
		TableBodyCell,
		TableBodyRow,
		TableHead,
		TableHeadCell
	} from 'flowbite-svelte';

	let tdheadClass = 'px-6 py-4 whitespace-normal font-medium bg-stone-800 text-stone-50';
	let tdrowClass = 'border-stone-200';
	let tdClass = 'px-6 py-4 whitespace-normal font-medium bg-stone-700 min-w-48';
	let tdClasss = 'px-6 py-4 whitespace-normal font-medium bg-stone-800 min-w-48';

	let code = `
public FadeUIElement(
  MonoBehaviour coroutineRunner, 
  VisualElement visualElement, 
  EasingMode easingMode = EasingMode.EaseOutCirc, 
  bool debug = false)`;
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl">Example: Multi Page UI</Heading>
<div class="p-4 max-w-5xl">
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>MultiPageUI</Heading
	>
	<P class="mb-4">
		You can find this example in Components sample.
	</P>
	<CodeBlock
		language="csharp"
		code={`
using CupkekGames.Core;
using UnityEngine.UIElements;

namespace CupkekGames.UITK.Demo.Components
{
    public class MultiPageUI : UIViewComponent
    {
        // Views
        private UIView _modal;
        private UIView _modalPageFirst;
        private UIView _modalPageSecond;

        // Buttons
        private Button _openModal;
        private Button _next;
        private Button _previous;

        protected override void Awake()
        {
            base.Awake();

            // Initialize the modal as a hidden UIView
            _modal = new UIView(gameObject, ParentElement.Q<VisualElement>("Modal"), UIStartVisibility.Invisible);

            // Initialize the first page of the modal and make it visible initially
            _modalPageFirst = new UIView(
                gameObject,
                _modal.ParentElement.Q<VisualElement>("Page1"),
                UIStartVisibility.Visible
            );

            // Initialize the second page of the modal and keep it hidden initially
            _modalPageSecond = new UIView(
                gameObject,
                _modal.ParentElement.Q<VisualElement>("Page2"),
                UIStartVisibility.Invisible
            );

            // Add an escape action to the modal to close it when triggered
            _modal.AddAction(new UIViewActionEscape(CloseModal));
            // Add an escape action to the second page to navigate back to the first page
            _modalPageSecond.AddAction(new UIViewActionEscape(() => ModalGoToPage(0)));

            // Retrieve button elements from the UI and assign them to variables
            _openModal = ParentElement.Q<Button>("OpenModal");
            _next = _modal.ParentElement.Q<Button>("Next");
            _previous = _modal.ParentElement.Q<Button>("Prev");
        }

        private void OnEnable()
        {
            // Register button click event handlers
            _openModal.clicked += OpenModal;
            _previous.clicked += InputEscapeManager.OnEscape; // Trigger the escape action
            _next.clicked += NextPage;
        }

        private void OnDisable()
        {
            // Unregister button click event handlers to avoid memory leaks
            _openModal.clicked -= OpenModal;
            _previous.clicked -= InputEscapeManager.OnEscape;
            _next.clicked -= NextPage;
        }

        public void OpenModal()
        {
            _modal.Fade.FadeIn();
        }

        public void CloseModal()
        {
            _modal.Fade.FadeOut();
        }

        public void ModalGoToPage(int index)
        {
            if (index == 0)
            {
                _modalPageFirst.Fade.FadeIn();
                _modalPageSecond.Fade.FadeOut();
            }
            else if (index == 1)
            {
                _modalPageFirst.Fade.FadeOut();
                _modalPageSecond.Fade.FadeIn();
            }
        }

        private void NextPage()
        {
            if (!_modalPageSecond.IsEnabled)
            {
                ModalGoToPage(1);
            }
        }
    }
}`}
		showHeader={true}
		showLineNumbers={true}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Nested UIViews</Heading
	>
	<P class="mb-4">
		I will elaborate on the problem and solution by building upon the example provided above.
	</P>
  <Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl"
		>Add an Action to first page</Heading
	>
	<CodeBlock
		language="csharp"
		code={`
// Add a UIViewActionEscape with Debug.Log to _modalPageFirst

// Set the second parameter, bool activate, to false because we don't want Action to register immediately.
// Because even of _modalPageFirst is visible, it's parent _modal is invisible.
// Otherwise, this Action will register at the start, when modal is closed.
_modalPageFirst.AddAction(new UIViewActionEscape(() => Debug.Log("First page: Can't escape me!")), false);`}
		showHeader={true}
		showLineNumbers={true}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
  <Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl"
		>Problem</Heading
	>
	<P class="mb-4">
		Actions such as UIViewActionEscape are registered when a UIView fades in. However, if you control the visibility of a UIView through a parent UIView, the actions of the child UIView will not be registered.
	</P>
	<P class="mb-4">
		In this case, we are controlling visibility with the parent _modal and we never fade _modalPageFirst directly. This means the Action we added to _modalPageFirst will never activate.
	</P>
  <Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl"
		>Solution</Heading
	>
	<P class="mb-4">
		To fix this issue, simply use AddChild function.
	</P>
	<CodeBlock
		language="csharp"
		code={`
_modal.AddChild(_modalPageFirst);`}
		showHeader={true}
		showLineNumbers={true}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<P class="my-4">
		With this, the Actions of child _modalPageFirst will register/unregister in sync with the parent _modal. 
    So when _modal fades in, the UIViewActionEscape with debug message will be registered and next escape input will print the message to the console.
	</P>
</div>
