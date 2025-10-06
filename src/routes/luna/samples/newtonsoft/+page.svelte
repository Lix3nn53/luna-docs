<script>
	import { Heading, P, Alert, A } from 'flowbite-svelte';

	import { CodeBlock } from 'svhighlight';
	import 'highlight.js/styles/base16/papercolor-dark.css';
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl"
	>Samples/ Newtonsoft JSON</Heading
>
<div class="p-4">
	<P class="mb-2">
		This sample demonstrates a complete file-based save system using Newtonsoft JSON within Luna. It shows how to implement a concrete save manager that works seamlessly with Luna's UI components.
	</P>

	<P class="pt-4">
		Refer to <A color="text-sky-400 font-extrabold" href="/luna/solutions/savesystem">Save System Framework</A> to learn about the UI-agnostic save system architecture.
	</P>

	<Alert border class="my-4">
		<div class="flex flex-row">
			<i class="fa-solid fa-lightbulb fa-2xl mr-4 mt-4"></i>
			<div>
				<P class="mb-2">
					<b>Key Features:</b> Pluggable serializers, secure type allow-lists, fast metadata loading, and complete UI integration.
				</P>
			</div>
		</div>
	</Alert>

	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>What You Get</Heading
	>
	<ul class="list-disc ml-6 space-y-1">
		<li><code>GameSaveManagerExample</code> — concrete manager handling files, folders, and JSON IO</li>
		<li><code>GameSaveDataExample</code> — example player/save data model</li>
		<li><code>GameSaveMetadataExample</code> — lightweight metadata for lists and previews</li>
		<li><code>InitializeSerializerExample</code> — safe serializer initialization with converters and type allow-list</li>
	</ul>

	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Quick Start</Heading
	>

	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>1. Initialize Serializer</Heading
	>
	<P>Add the serializer initializer to your bootstrap scene:</P>
	<CodeBlock
		language="csharp"
		code={`_serializationManager.Initialize(
    new Type[] {
        typeof(GameSaveMetadata),
        typeof(GameSaveMetadataExample),
        typeof(GameSaveDataExample),
        typeof(Inventory),
        typeof(InventoryItem),
        typeof(Potion),
        typeof(Equipment),
    },
    new JsonConverter[] {
        new Vector2IntConverter(),
        new GenericDictionaryConverter()
    },
    new PrivateSetterContractResolver()
);`}
		showHeader={true}
		showLineNumbers={true}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>

	<Alert border class="my-4">
		<div class="flex flex-row">
			<i class="fa-solid fa-shield fa-2xl mr-4 mt-4"></i>
			<div>
				<P class="mb-2">
					Keep the type allow-list tight for security when using <code>TypeNameHandling</code> features.
				</P>
			</div>
		</div>
	</Alert>

	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>2. Create Save Data Classes</Heading
	>
	<CodeBlock
		language="csharp"
		code={`public class MyGameSaveData : IGameSaveData {
    [JsonProperty(Order = -100)]
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
		>3. Create Metadata Class</Heading
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

	<Alert border class="my-4">
		<div class="flex flex-row">
			<i class="fa-solid fa-info-circle fa-2xl mr-4 mt-4"></i>
			<div>
				<P class="mb-2">
					Use <code>[JsonProperty(Order = -100)]</code> on <code>Metadata</code> so it appears first in JSON for fast metadata reads.
				</P>
			</div>
		</div>
	</Alert>

	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>4. Implement Save Manager</Heading
	>
	<P>Inherit from <code>GameSaveManager&lt;MyGameSaveData, MyGameSaveMetadata&gt;</code> and implement the JSON-specific methods:</P>
	<CodeBlock
		language="csharp"
		code={`public class MyGameSaveManager : GameSaveManager<MyGameSaveData, MyGameSaveMetadata> {
    
    protected override string[] GetAllFileNames() {
        // Enumerate .json files in save directory
        return Directory.GetFiles(GetSaveDirectory(), "*.json")
                       .Select(Path.GetFileName)
                       .ToArray();
    }

    protected override MyGameSaveData GetNewSave(string saveVersion) {
        return new MyGameSaveData();
    }

    protected override void OnSaveRequest(int saveSlot, string fileName, 
        MyGameSaveData data, bool autosave) {
        // Serialize and write JSON file
        string json = JsonConvert.SerializeObject(data, Formatting.Indented);
        File.WriteAllText(Path.Combine(GetSaveDirectory(), fileName), json);
    }

    protected override MyGameSaveData LoadFromFile(string fileName) {
        // Deserialize full save data
        string json = File.ReadAllText(Path.Combine(GetSaveDirectory(), fileName));
        return JsonConvert.DeserializeObject<MyGameSaveData>(json);
    }

    protected override MyGameSaveMetadata LoadMetadataFromFile(string fileName) {
        // Fast path to read only metadata
        using var reader = new JsonTextReader(new StringReader(
            File.ReadAllText(Path.Combine(GetSaveDirectory(), fileName))));
        
        while (reader.Read()) {
            if (reader.TokenType == JsonToken.PropertyName && 
                reader.Value?.ToString() == "Metadata") {
                reader.Read();
                return JsonConvert.DeserializeObject<MyGameSaveMetadata>(
                    reader.ReadAsString());
            }
        }
        return null;
    }

    protected override void OnDeleteRequest(int saveSlot, string fileName) {
        // Delete JSON file
        File.Delete(Path.Combine(GetSaveDirectory(), fileName));
    }

    protected override string GetFileExtension() => "json";
    protected override string GetSaveVersion() => "1.0";
}`}
		showHeader={true}
		showLineNumbers={true}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>

	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>UI Integration</Heading
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
		>File Locations</Heading
	>
	<ul class="list-disc ml-6 space-y-1">
		<li><b>Save Directory:</b> <code>Application.persistentDataPath/saves/</code></li>
		<li><b>File Extension:</b> <code>.json</code> (configured by your manager)</li>
		<li><b>Version:</b> Set via <code>GetSaveVersion()</code> method</li>
	</ul>

	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Advanced Features</Heading
	>

	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>Encryption</Heading
	>
	<P>Add encryption/decryption in your manager's save/load methods:</P>
	<CodeBlock
		language="csharp"
		code={`protected override void OnSaveRequest(int saveSlot, string fileName, 
    MyGameSaveData data, bool autosave) {
    string json = JsonConvert.SerializeObject(data, Formatting.Indented);
    byte[] encrypted = Encrypt(json); // Your encryption logic
    File.WriteAllBytes(Path.Combine(GetSaveDirectory(), fileName), encrypted);
}

protected override MyGameSaveData LoadFromFile(string fileName) {
    byte[] encrypted = File.ReadAllBytes(Path.Combine(GetSaveDirectory(), fileName));
    string json = Decrypt(encrypted); // Your decryption logic
    return JsonConvert.DeserializeObject<MyGameSaveData>(json);
}`}
		showHeader={false}
		showLineNumbers={true}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>

	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>Cloud Storage</Heading
	>
	<P>Replace file IO with cloud API calls while keeping the same UI interface:</P>
	<CodeBlock
		language="csharp"
		code={`protected override void OnSaveRequest(int saveSlot, string fileName, 
    MyGameSaveData data, bool autosave) {
    string json = JsonConvert.SerializeObject(data);
    CloudStorage.Upload(fileName, json); // Your cloud API
}

protected override MyGameSaveData LoadFromFile(string fileName) {
    string json = CloudStorage.Download(fileName); // Your cloud API
    return JsonConvert.DeserializeObject<MyGameSaveData>(json);
}`}
		showHeader={false}
		showLineNumbers={true}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>

	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Troubleshooting</Heading
	>

	<div class="space-y-4">
		<Alert border>
			<div class="flex flex-row">
				<i class="fa-solid fa-exclamation-triangle fa-2xl mr-4 mt-4"></i>
				<div>
					<Heading tag="h4" class="font-bold mb-2">No save files found</Heading>
					<P class="mb-2">
						Ensure <code>Application.persistentDataPath/saves</code> exists and the platform has write permissions.
					</P>
				</div>
			</div>
		</Alert>

		<Alert border>
			<div class="flex flex-row">
				<i class="fa-solid fa-exclamation-triangle fa-2xl mr-4 mt-4"></i>
				<div>
					<Heading tag="h4" class="font-bold mb-2">Metadata shows null</Heading>
					<P class="mb-2">
						Ensure <code>Metadata</code> is serialized first with <code>[JsonProperty(Order = -100)]</code> and created before saving.
					</P>
				</div>
			</div>
		</Alert>

		<Alert border>
			<div class="flex flex-row">
				<i class="fa-solid fa-exclamation-triangle fa-2xl mr-4 mt-4"></i>
				<div>
					<Heading tag="h4" class="font-bold mb-2">Deserialization errors</Heading>
					<P class="mb-2">
						Update the serializer allow-list and add required converters for custom types.
					</P>
				</div>
			</div>
		</Alert>

		<Alert border>
			<div class="flex flex-row">
				<i class="fa-solid fa-exclamation-triangle fa-2xl mr-4 mt-4"></i>
				<div>
					<Heading tag="h4" class="font-bold mb-2">UI buttons disabled</Heading>
					<P class="mb-2">
						Verify your manager returns valid metadata from <code>GetLastMetadata()</code> and the serializer is properly initialized.
					</P>
				</div>
			</div>
		</Alert>
	</div>

	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Best Practices</Heading
	>
	<ul class="list-disc ml-6 space-y-1">
		<li>Use <code>[JsonProperty(Order = -100)]</code> on Metadata for fast metadata reads</li>
		<li>Implement fast metadata loading to avoid deserializing full saves for UI lists</li>
		<li>Keep type allow-lists minimal for security when using TypeNameHandling</li>
		<li>Handle version migration in your load methods for schema changes</li>
		<li>Use autosave functionality built into the manager</li>
		<li>Test save/load on target platforms early in development</li>
	</ul>

	<Alert border class="my-4">
		<div class="flex flex-row">
			<i class="fa-solid fa-circle-info fa-2xl mr-4 mt-4"></i>
			<div>
				<P class="mb-2">
					<b>Remember:</b> The UI remains completely unchanged when you swap between JSON, binary, cloud, or encrypted storage. Only your manager implementation changes.
				</P>
			</div>
		</div>
	</Alert>
</div>
