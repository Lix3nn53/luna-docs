<script>
	import { Heading, P, Alert } from 'flowbite-svelte';
	import draganddrop from '$lib/img/docs/framework/dragdrop.jpg';

	import { CodeBlock } from 'svhighlight';
	import 'highlight.js/styles/base16/papercolor-dark.css';
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl"
	>Framework/ Drag & Drop</Heading
>
<div class="p-4">
	<img alt="draganddrop" src={draganddrop} class="mb-6 max-w-2xl rounded-xl border-4" />
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Example Usage</Heading
	>
	<P>
		As always, you can find this example in the Components sample.
	</P>
	<Alert border>
		<div class="flex flex-row">
			<i class="fa-solid fa-circle-info fa-2xl mr-4 mt-4"></i>
			<div>
				<P class="mb-4"
					>For more advanced example, refer to Inventory implementation in Game samples.</P
				>
			</div>
		</div>
	</Alert>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl"
		>DragAndDropManipulator</Heading
	>
	<P>
	Manipulator to add to VisualElements that will start drag operation.
	</P>
	<CodeBlock
		language="csharp"
		code={`
using System;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UIElements;

namespace CupkekGames.UITK.Demo.Components
{
    public class DragAndDropManipulatorDemo : DragAndDropManipulator
    {
        // Custom Data
        private Sprite _background;

        // Custom OnDrop event
        // Demonstrates the use of DisposeDragElement
        // Parameters: drop slot and _background sprite
        public event Action<VisualElement, Sprite> ExampleOnDropEvent;

        public DragAndDropManipulatorDemo(
            UIElementManager uiElementManager,
            VisualElement dragArea, int key,
            List<VisualElement> dropSlots,
            Func<List<VisualElement>> getDropSlots,
            Sprite background)
         : base(uiElementManager, dragArea, key, dropSlots, getDropSlots)
        {
            _background = background;
        }

        // Called when dragging starts
        public override VisualElement CreateDragElement()
        {
            // Create and style a new VisualElement for the drag operation
            VisualElement dragElement = new VisualElement();
            dragElement.AddToClassList("size-128");
            dragElement.AddToClassList("rounded-lg");
            dragElement.AddToClassList("bg-base-600");
            dragElement.AddToClassList("border-4");
            dragElement.AddToClassList("border-base-50");

            // Set background image
            dragElement.style.backgroundImage = new StyleBackground(_background);

            // Register custom event with the OnDrop event
            OnDrop += OnItemDropInner;

            return dragElement;
        }

        // Called when dragging ends
        public override void DisposeDragElement()
        {
            // Unregister custom event from the OnDrop event
            OnDrop -= OnItemDropInner;
        }

        private void OnItemDropInner(int key, int dropIndex, VisualElement dropSlot)
        {
            // Invoke the custom event, passing the drop slot and background sprite
            ExampleOnDropEvent?.Invoke(dropSlot, _background);
        }
    }
}`}
		showHeader={true}
		showLineNumbers={true}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl"
		>DragAndDropDemo</Heading
	>
	<CodeBlock
		language="csharp"
		code={`
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UIElements;

namespace CupkekGames.UITK.Demo.Components
{
    public class DragAndDropDemo : UIViewComponent
    {
        // Images to use as data of this demo
        [SerializeField] Sprite[] _images;

        protected override void Awake()
        {
            base.Awake();

            // Get drag starter elements
            List<VisualElement> dragStarters = ParentElement.Query<VisualElement>("DragStarter").ToList();
            // Get drop slot elements
            List<VisualElement> dropSlots = ParentElement.Query<VisualElement>("DropSlot").ToList();

            // Setup drag starters
            for (int i = 0; i < dragStarters.Count; i++)
            {
                VisualElement dragStarter = dragStarters[i];

                Sprite image = _images[i];
                dragStarter.style.backgroundImage = new StyleBackground(image);

                // Create manipulator
                DragAndDropManipulatorDemo manipulator = new DragAndDropManipulatorDemo(
                    null, // UIElementManager can be null. Refer to the documentation for its usage in DragAndDropManipulator.
                    ParentElement, // The drag area.
                    i, // Key identifier for the manipulator.
                    dropSlots, // Predefined drop slots.
                    null, // Optional dynamic drop slots, if needed.
                    image // Custom data specific to the demo.
                );

                // Register to event
                manipulator.ExampleOnDropEvent += OnDrop;

                // Create manipulator to dragStarter
                dragStarter.AddManipulator(manipulator);
            }
        }

        private void OnDrop(VisualElement dropSlot, Sprite _background)
        {
            // Change the dropSlot's background image
            dropSlot.style.backgroundImage = new StyleBackground(_background);
        }
    }
}`}
		showHeader={true}
		showLineNumbers={true}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>DragAndDropManipulator</Heading
	>
	<P>
		DragAndDropManipulator is the base class you can inherit from to create custom Drag & Drop operations easily.
	</P>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl"
		>Contructors</Heading
	>
	<CodeBlock
		language="csharp"
		code={`
public DragAndDropManipulator(
  UIElementManager uiElementManager, // UIElementManager can be null. Look below for its usage in DragAndDropManipulator.
  VisualElement dragArea, // The drag area.
  int key, // Key identifier for the manipulator. It's not required, but useful for identifying elements.
  List<VisualElement> dropSlots, // Predefined drop slots.
  Func<List<VisualElement>> getDropSlots = null // Optional dynamic drop slots, if needed.
)`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl"
		>UIElementManager?</Heading
	>
  <P>UIElementManager's purpose in DragAndDropManipulator is to prevent hover audio from playing when hovering over other buttons and interactable elements while dragging an element.</P>
  <P>When a drag operation starts, if UIElementManager is not null, hover audio will be muted until the drag operation ends.</P>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl"
		>Public Methods</Heading
	>
	<Heading tag="h4" class="my-2" customSize="text-md font-bold md:text-lg lg:text-xl"
		>CreateDragElement</Heading
	>
  <P>Called when drag operation starts.</P>
  <P>Override to create the drag element, initialize the logic, and register event handlers, etc.</P>
	<CodeBlock
		language="csharp"
		code={`public abstract VisualElement CreateDragElement();`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h4" class="my-2" customSize="text-md font-bold md:text-lg lg:text-xl"
		>DisposeDragElement</Heading
	>
  <P>Called when drag operation ends.</P>
  <P>Override to dispose of the drag element, clean up logic, and unregister event handlers, etc.</P>
	<CodeBlock
		language="csharp"
		code={`public abstract void DisposeDragElement();`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl"
		>Events</Heading
	>
	<Heading tag="h4" class="my-2" customSize="text-md font-bold md:text-lg lg:text-xl"
		>OnStart{"<Vector3>"}</Heading
	>
  <P>First parameter is pointerPosition.</P>
	<Heading tag="h4" class="my-2" customSize="text-md font-bold md:text-lg lg:text-xl"
		>OnMove{"<Vector3>"}</Heading
	>
  <P>First parameter is pointerPosition.</P>
	<Heading tag="h4" class="my-2" customSize="text-md font-bold md:text-lg lg:text-xl"
		>OnDrop{"<int, int, VisualElement>"}</Heading
	>
  <P>First parameter is key.</P>
  <P>Second parameter is the index of the drop slot where the element was dropped.</P>
  <P>Second parameter is the drop slot where the element was dropped.</P>
	<Heading tag="h4" class="my-2" customSize="text-md font-bold md:text-lg lg:text-xl"
		>OnCancel</Heading
	>
</div>
