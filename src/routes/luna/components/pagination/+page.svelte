<script>
	import { Heading, P } from 'flowbite-svelte';
	import pagination from '$lib/img/docs/components/pagination.jpg';

	import { CodeBlock } from 'svhighlight';
	import 'highlight.js/styles/base16/papercolor-dark.css';
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl"
	>Components/ Pagination</Heading
>
<div class="p-4">
	<img alt="pagination" src={pagination} class="mb-6 max-w-2xl rounded-xl border-4" />
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Example Usage</Heading
	>
	<P>
		As always, you can find this example in the Components sample.
	</P>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl"
		>LabelWithBinding</Heading
	>
	<P>
	Create an UI controller class named LabelWithBinding. This allows us to reuse existing elements, instead of deleting and recreating elements at runtime.
	</P>
	<P>
	This approach improves performance by reducing garbage collection overhead and ensures smoother UI updates.
	</P>
	<CodeBlock
		language="csharp"
		code={`
using UnityEngine.UIElements;

namespace CupkekGames.UITK.Demo.Components
{
    public class LabelWithBinding
    {
        private Label _label;

        public LabelWithBinding(Label label)
        {
            _label = label;
        }

        public void Bind(string data)
        {
            _label.text = data;
        }

        public void Unbind()
        {
            _label.text = "";
        }
    }
}`}
		showHeader={true}
		showLineNumbers={true}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl"
		>PaginationDemo</Heading
	>
	<CodeBlock
		language="csharp"
		code={`
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UIElements;

namespace CupkekGames.UITK.Demo.Components
{
    public class PaginationDemo : UIViewComponent
    {
        // Settings
        [Header("Pagination Settings")]
        [SerializeField] private int _itemPerPage = 3;
        [SerializeField] private int _maxButtonAmount = 5;
        [SerializeField] private UIColorName _baseButtonColor = UIColorName.BASE;
        [SerializeField] private UIColorName _activeButtonColor = UIColorName.PRIMARY;
        [Header("Pagination Data")]
        [SerializeField] private int _dataAmount = 200;
        // Pagination
        private PaginationController<string> _pagination;

        // Source List
        private List<string> _sourceList = new();
        // UI Controller for page elements
        private List<LabelWithBinding> _uiController = new();

        // Container
        private VisualElement _container;

        protected override void Awake()
        {
            base.Awake();

            // Mock up data
            for (int i = 0; i < _dataAmount; i++)
            {
                _sourceList.Add("Element-" + i);
            }

            // Create page element controllers  
            // In this example, our controller class is LabelWithBinding.  
            // Using controllers allows us to reuse VisualElements instead of destroying  
            // and recreating them whenever the page changes.  
            // This approach improves performance and reduces unnecessary UI rebuilds.  
            _container = ParentElement.Q<VisualElement>("PaginationElementsContainer");
            for (int i = 0; i < _itemPerPage; i++)
            {
                Label label = new Label();
                _container.Add(label);
                LabelWithBinding uiController = new LabelWithBinding(label);
                _uiController.Add(uiController);
            }

            // Create pagination
            VisualElement paginationElement = ParentElement.Q<VisualElement>("Pagination");
            _pagination = new(
                _sourceList,
                _itemPerPage,
                paginationElement,
                _baseButtonColor,
                _activeButtonColor,
                _maxButtonAmount
            );
        }

        private void OnEnable()
        {
            _pagination.OnPageChange += OnPageChange;
        }

        private void OnDisable()
        {
            _pagination.OnPageChange -= OnPageChange;
        }

        protected virtual void Start()
        {
            // Render first page
            _pagination.GoToPage(0);
        }

        private void OnPageChange(int page)
        {
            List<string> currentPage = _pagination.GetCurrentPageElements(); // get data for current page

            // int start = _pagination.GetStartIndex(page); // get start index of current page if needed

            // Why binding?
            // Instead of deleting and recreating elements at runtime, 
            // we are reusing existing elements and updating their content dynamically.
            // This approach improves performance by reducing garbage collection overhead 
            // and ensures smoother UI updates.

            for (int i = 0; i < _pagination.ItemsPerPage; i++)
            {
                LabelWithBinding controller = _uiController[i];
                controller.Unbind();

                if (i >= currentPage.Count)
                {
                    continue;
                }

                // Alternative way to get data
                // int index = start + i;
                // string data = _sourceList[index];

                // Easier way to get data
                string data = currentPage[i];

                controller.Bind(data);
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
		>Pagination{"<T>"}</Heading
	>
	<P>
		Pagination{"<T>"} is the base class for controlling data, without any relation to UI.
	</P>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl"
		>Contructors</Heading
	>
	<CodeBlock
		language="csharp"
		code={`public Pagination(List<T> data, int itemsPerPage)`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl"
		>Public Methods</Heading
	>
	<Heading tag="h4" class="my-2" customSize="text-md font-bold md:text-lg lg:text-xl"
		>NextPage</Heading
	>
	<CodeBlock
		language="csharp"
		code={`
// Returns true if page changed
public bool NextPage()`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h4" class="my-2" customSize="text-md font-bold md:text-lg lg:text-xl"
		>PreviousPage</Heading
	>
	<CodeBlock
		language="csharp"
		code={`
// Returns true if page changed
public bool PreviousPage()`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h4" class="my-2" customSize="text-md font-bold md:text-lg lg:text-xl"
		>GoToPage</Heading
	>
	<CodeBlock
		language="csharp"
		code={`
// Returns true if page changed
public bool GoToPage(int pageIndex)`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h4" class="my-2" customSize="text-md font-bold md:text-lg lg:text-xl"
		>GetCurrentPageElements</Heading
	>
	<CodeBlock
		language="csharp"
		code={`
// Returns list of elements that belongs to current page
public List<T> GetCurrentPageElements()`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h4" class="my-2" customSize="text-md font-bold md:text-lg lg:text-xl"
		>GoToPage</Heading
	>
	<CodeBlock
		language="csharp"
		code={`
// Returns start index of curent page
public int GetStartIndex(int page)`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl"
		>Events</Heading
	>
	<Heading tag="h4" class="my-2" customSize="text-md font-bold md:text-lg lg:text-xl"
		>OnPageChange</Heading
	>
	<CodeBlock
		language="csharp"
		code={`public event Action<int> OnPageChange; // int parameter is the new page index`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>PaginationController{"<T>"}</Heading
	>
	<P>
		PaginationController{"<T>"} is the UI controller class that makes use of Pagination{"<T>"}.
	</P>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl"
		>Contructors</Heading
	>
	<CodeBlock
		language="csharp"
		code={`
// Creates pagination without setting up the UI.
// You can later use SetUI function to setup the UI.
public PaginationController(List<T> data, int itemsPerPage)

// Creates pagination and setups the UI.
public PaginationController(
	List<T> data, // data source
	int itemsPerPage, // how many items to show in one page
	VisualElement parent, // Parent element, usually the UXML of pagination component
	UIColorName normal, // Default color of buttons
	UIColorName active, // Color of active page's button
	int maxButtonAmount // maximum amount of pagination buttons
)`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl"
		>Public Methods</Heading
	>
	<Heading tag="h4" class="my-2" customSize="text-md font-bold md:text-lg lg:text-xl"
		>SetUI</Heading
	>
	<CodeBlock
		language="csharp"
		code={`public void SetUI(VisualElement parent, UIColorName normal, UIColorName active, int maxButtonAmount)`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h4" class="my-2" customSize="text-md font-bold md:text-lg lg:text-xl"
		>UpdateUI</Heading
	>
	<CodeBlock
		language="csharp"
		code={`
// Updates pagination elements by re-creating them
public void UpdateUI()`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h4" class="my-2" customSize="text-md font-bold md:text-lg lg:text-xl"
		>Show</Heading
	>
	<CodeBlock
		language="csharp"
		code={`public void Show()`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h4" class="my-2" customSize="text-md font-bold md:text-lg lg:text-xl"
		>Hide</Heading
	>
	<CodeBlock
		language="csharp"
		code={`public void Hide()`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
</div>
