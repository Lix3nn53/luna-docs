<script>
	import { Heading, P, Alert, A } from 'flowbite-svelte';

	import { CodeBlock } from 'svhighlight';
	import 'highlight.js/styles/base16/papercolor-dark.css';
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl"
	>Systems/ Save System</Heading
>
<div class="p-4">
	<P>
		Luna's save system framework provides UI components that work with any save implementation through a clean abstraction layer. Your UI remains unchanged whether you use JSON files, binary data, cloud storage, or encrypted saves.
	</P>

	<Alert border class="my-4">
		<div class="flex flex-row">
			<i class="fa-solid fa-lightbulb fa-2xl mr-4 mt-4"></i>
			<div>
				<P class="mb-2">
					<b>Key Benefits:</b> UI-agnostic design, pluggable save implementations, fast metadata loading, and seamless integration with Luna's UI components.
				</P>
			</div>
		</div>
	</Alert>

	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Core Concepts</Heading
	>
	<div class="space-y-4">
		<div class="bg-gray-50 dark:bg-gray-800 p-4 rounded-lg">
			<Heading tag="h3" class="text-lg font-semibold mb-2">UI Components</Heading>
			<P>Luna provides pre-built UI components like MainMenuView and GameSaveView that handle save/load operations automatically.</P>
		</div>
		<div class="bg-gray-50 dark:bg-gray-800 p-4 rounded-lg">
			<Heading tag="h3" class="text-lg font-semibold mb-2">GameSaveManager&lt;TData,TMeta&gt;</Heading>
			<P>Abstract interface that connects your save implementation to Luna's UI. You provide the concrete implementation.</P>
		</div>
		<div class="bg-gray-50 dark:bg-gray-800 p-4 rounded-lg">
			<Heading tag="h3" class="text-lg font-semibold mb-2">Save Data Types</Heading>
			<P>Your game defines the save data structure (TSaveData) and metadata (TSaveMetadata) that the UI will work with.</P>
		</div>
	</div>

	<P class="my-4">
		The beauty of Luna's save system is that your UI code never changes. Whether you implement JSON files, binary data, cloud storage, or encrypted saves, the UI components work identically through the manager interface.
	</P>

	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Quick Start</Heading
	>

	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>1. Define Your Save Data</Heading
	>
	<P>Create your save data class that implements <code>IGameSaveData</code>:</P>
	<CodeBlock
		language="csharp"
		code={`public class MyGameSaveData : IGameSaveData {
    public GameSaveMetadata Metadata { get; set; }
    public string PlayerName;
    public int Gold;
    public Inventory Inventory;

    public MyGameSaveData() {
        PlayerName = "Player";
        Gold = 0;
        Inventory = new Inventory();
    }

    public GameSaveMetadata CreateMetadata(string saveVersion, bool isAutosave) {
        return new MyGameSaveMetadata {
            SaveVersion = saveVersion,
            SaveDate = DateTime.Now,
            IsAutosave = isAutosave,
            Gold = Gold,
        };
    }

    public void LoadFrom(IGameSaveData other, int slot) {
        var o = (MyGameSaveData)other;
        Metadata = o.Metadata;
        PlayerName = o.PlayerName;
        Gold = o.Gold;
        Inventory = o.Inventory;
    }
}`}
		showHeader={true}
		showLineNumbers={true}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>

	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>2. Create Metadata Class</Heading
	>
	<P>Define lightweight metadata for UI display:</P>
	<CodeBlock
		language="csharp"
		code={`public class MyGameSaveMetadata : GameSaveMetadata {
    public int Gold;
}`}
		showHeader={false}
		showLineNumbers={true}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>

	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>3. Implement Save Manager</Heading
	>
	<P>Inherit from <code>GameSaveManager&lt;TSaveData, TSaveMetadata&gt;</code> and implement the required methods:</P>
	<CodeBlock
		language="csharp"
		code={`public class MyGameSaveManager : GameSaveManager<MyGameSaveData, MyGameSaveMetadata> {
    
    // Enumerate all save files
    protected override string[] GetAllFileNames() {
        // Your implementation here - could be files, cloud entries, etc.
        return Directory.GetFiles(GetSaveDirectory(), "*.sav")
                       .Select(Path.GetFileName)
                       .ToArray();
    }

    // Create a new save instance
    protected override MyGameSaveData GetNewSave(string saveVersion) {
        return new MyGameSaveData();
    }

    // Save data to storage
    protected override void OnSaveRequest(int saveSlot, string fileName, 
        MyGameSaveData data, bool autosave) {
        // Your save implementation - could be JSON, binary, cloud, etc.
        // Example: File.WriteAllBytes(Path.Combine(GetSaveDirectory(), fileName), serializedData);
    }

    // Load full save data
    protected override MyGameSaveData LoadFromFile(string fileName) {
        // Your load implementation
        // Example: return DeserializeData(File.ReadAllBytes(...));
        return null;
    }

    // Load only metadata (for fast UI loading)
    protected override MyGameSaveMetadata LoadMetadataFromFile(string fileName) {
        // Fast path to read only metadata without loading full save
        return null;
    }

    protected override string GetFileExtension() => "sav";
    protected override string GetSaveVersion() => "1.0";
}`}
		showHeader={true}
		showLineNumbers={true}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>

	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>4. Connect to Luna UI</Heading
	>
	<P>Wire your manager into Luna UI components by overriding the provider method:</P>

	<CodeBlock
		language="csharp"
		code={`public class MyMainMenuView : MainMenuView<MyGameSaveData, MyGameSaveMetadata> {
    
    [SerializeField] private MyGameSaveManager saveManager;
    
    protected override GameSaveManager<MyGameSaveData, MyGameSaveMetadata> GetSaveManager() {
        return saveManager;
    }
}`}
		showHeader={true}
		showLineNumbers={true}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>

	<Alert border class="my-4">
		<div class="flex flex-row">
			<i class="fa-solid fa-magic-wand-sparkles fa-2xl mr-4 mt-4"></i>
			<div>
				<P class="mb-2">
					Once connected, UI buttons (Continue, Load, New Game, Delete) automatically work through your manager. No additional UI code needed!
				</P>
			</div>
		</div>
	</Alert>

	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Available UI Components</Heading
	>
	<div class="space-y-4">
		<div class="bg-gray-50 dark:bg-gray-800 p-4 rounded-lg">
			<Heading tag="h3" class="text-lg font-semibold mb-2">MainMenuView&lt;TSaveData, TSaveMetadata&gt;</Heading>
			<P>Provides Continue, New Game, and Load Game buttons. Automatically enables Continue when a recent save exists.</P>
		</div>
		<div class="bg-gray-50 dark:bg-gray-800 p-4 rounded-lg">
			<Heading tag="h3" class="text-lg font-semibold mb-2">GameSaveView&lt;TSaveData, TSaveMetadata&gt;</Heading>
			<P>Displays save slots with metadata previews, handles save/load/delete operations.</P>
		</div>
	</div>

	<P class="pt-4">
		For detailed UI implementation examples, see:
		<A color="text-sky-400 font-extrabold" href="/luna/views/mainmenu">Main Menu</A> and 
		<A color="text-sky-400 font-extrabold" href="/luna/views/saveload">Save & Load</A> views. 
		Also available is the <A color="text-sky-400 font-extrabold" href="/luna/views/autosave">Autosave Notification</A> utility UI.
	</P>

	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Implementation Examples</Heading
	>

	<P>Your save manager can implement any storage format. For a complete working example with Newtonsoft JSON, see:</P>

	<Alert border class="my-4">
		<div class="flex flex-row">
			<i class="fa-solid fa-external-link-alt fa-2xl mr-4 mt-4"></i>
			<div>
				<P class="mb-2">
					Refer to <A color="text-sky-400 font-extrabold" href="/luna/samples/newtonsoft">Newtonsoft JSON Sample</A> for a complete working implementation with serializer initialization, converters, and file handling.
				</P>
			</div>
		</div>
	</Alert>
</div>