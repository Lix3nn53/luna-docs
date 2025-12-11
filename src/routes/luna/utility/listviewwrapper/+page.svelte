<script>
	import { Heading, P, Alert } from 'flowbite-svelte';

	import { CodeBlock } from 'svhighlight';
	import 'highlight.js/styles/base16/papercolor-dark.css';
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl"
	>Utility/ ListViewWrapper</Heading
>
<div class="p-4">
	<P>
		<b>ListViewWrapper</b> provides keyboard navigation functionality for Unity's <code>ListView</code> component. It prevents individual list items from receiving focus and handles Up/Down/Next/Previous navigation between items, making keyboard navigation feel natural.
	</P>

	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Quick Start</Heading
	>
	<CodeBlock
		language="csharp"
		code={`using CupkekGames.Luna;
using UnityEngine.UIElements;

public class MyListView : MonoBehaviour
{
    private ListView _listView;
    private ListViewWrapper _listViewWrapper;

    private void Awake()
    {
        _listView = GetComponent<UIDocument>().rootVisualElement.Q<ListView>("MyList");
        _listViewWrapper = new ListViewWrapper(_listView);
    }

    private void OnEnable()
    {
        _listViewWrapper.Enable();
    }

    private void OnDisable()
    {
        _listViewWrapper.Disable();
    }
}`}
		showHeader={true}
		showLineNumbers={true}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>

	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>API</Heading
	>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>Constructor</Heading
	>
	<CodeBlock
		language="csharp"
		code={`public ListViewWrapper(ListView listView)`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<P>
		Creates a new wrapper instance for the specified ListView.
	</P>

	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>Methods</Heading
	>
	<CodeBlock
		language="csharp"
		code={`public void Enable();                    // Enables keyboard navigation handlers
public void Disable();                   // Disables keyboard navigation handlers
public void ResetSelection();            // Resets selection to first item and focuses ListView
public bool ValidateSelection();         // Validates and adjusts selected index if out of bounds
public IDisposable RegisterAdjacentElementNavigation(
    VisualElement element,
    VisualElement horizontalTarget = null); // Registers bidirectional navigation with adjacent element`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>

	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>Properties</Heading
	>
	<CodeBlock
		language="csharp"
		code={`public ListView ListView { get; }                    // Access to the wrapped ListView
public bool AutoScrollOnSelectionChange { get; set; }  // Auto-scroll on selection changes (default: false)`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>

	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>Events</Heading
	>
	<CodeBlock
		language="csharp"
		code={`public event Action<NavigationContext> OnNavigateVertical;           // Fires on Up/Down/Next/Previous navigation
public event Action<NavigationMoveEvent.Direction> OnNavigateHorizontal; // Fires on Left/Right navigation
public event Func<NavigationMoveEvent.Direction, VisualElement> OnGetBoundaryNavigationTarget; // Fires at boundaries
public event Action<int> OnValidSelectionChanged;                      // Fires when selection changes to valid index`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>

	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Example: List with Return Button</Heading
	>
	<P>
		This example shows how to set up a ListView with a return button that handles boundary navigation.
	</P>
	<CodeBlock
		language="csharp"
		code={`using CupkekGames.Luna;
using UnityEngine.UIElements;

public class ListViewWithButton : MonoBehaviour
{
    private ListView _listView;
    private Button _returnButton;
    private ListViewWrapper _listViewWrapper;

    private void Awake()
    {
        var root = GetComponent<UIDocument>().rootVisualElement;
        _listView = root.Q<ListView>("MyList");
        _returnButton = root.Q<Button>("ReturnButton");
        
        _listViewWrapper = new ListViewWrapper(_listView);
        
        // Navigate to return button at boundaries
        _listViewWrapper.OnGetBoundaryNavigationTarget += (_) => _returnButton;
        
        // Navigate to return button on horizontal navigation
        _listViewWrapper.OnNavigateHorizontal += (_) => _returnButton.Focus();
        
        // Register bidirectional navigation
        _listViewWrapper.RegisterAdjacentElementNavigation(_returnButton);
    }

    private void OnEnable()
    {
        _listViewWrapper.Enable();
    }

    private void OnDisable()
    {
        _listViewWrapper.Disable();
    }
}`}
		showHeader={true}
		showLineNumbers={true}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>

	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Example: Selection Change Handling</Heading
	>
	<P>
		Handle selection changes safely using <code>OnValidSelectionChanged</code>.
	</P>
	<CodeBlock
		language="csharp"
		code={`using CupkekGames.Luna;
using UnityEngine.UIElements;

public class ListViewWithSelection : MonoBehaviour
{
    private ListView _listView;
    private ListViewWrapper _listViewWrapper;
    private List<ItemData> _dataList;

    private void Awake()
    {
        _listView = GetComponent<UIDocument>().rootVisualElement.Q<ListView>("MyList");
        _listViewWrapper = new ListViewWrapper(_listView);
        
        // Handle valid selection changes
        _listViewWrapper.OnValidSelectionChanged += OnSelectionChanged;
    }

    private void OnEnable()
    {
        _listViewWrapper.Enable();
    }

    private void OnDisable()
    {
        _listViewWrapper.Disable();
    }

    private void OnSelectionChanged(int index)
    {
        var selectedItem = _dataList[index];
        UpdateDetailsPanel(selectedItem);
    }

    private void UpdateDetailsPanel(ItemData item)
    {
        // Update UI with selected item data
    }
}`}
		showHeader={true}
		showLineNumbers={true}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>

	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Example: Dynamic Data Updates</Heading
	>
	<P>
		Validate selection after changing the data source.
	</P>
	<CodeBlock
		language="csharp"
		code={`private void UpdateData(List<ItemData> newData)
{
    _listView.itemsSource = newData;
    _listView.RefreshItems();
    
    // Validate selection after data change
    if (_listViewWrapper.ValidateSelection())
    {
        // Selection was adjusted, update UI
        if (_listView.selectedIndex >= 0)
        {
            OnSelectionChanged(_listView.selectedIndex);
        }
    }
    else if (_listView.selectedIndex >= 0)
    {
        // Selection is still valid
        OnSelectionChanged(_listView.selectedIndex);
    }
}`}
		showHeader={true}
		showLineNumbers={true}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>

	<Alert border class="my-4">
		<div class="flex flex-row">
			<i class="fa-solid fa-circle-info fa-2xl mr-4 mt-4"></i>
			<div>
				<P class="mb-2">
					Always call <code>Enable()</code> when your view becomes active and <code>Disable()</code> when it becomes inactive to prevent memory leaks.
				</P>
				<P class="mb-2">
					Use <code>OnValidSelectionChanged</code> instead of ListView's <code>selectionChanged</code> to ensure you only handle valid selections.
				</P>
			</div>
		</div>
	</Alert>
</div>

