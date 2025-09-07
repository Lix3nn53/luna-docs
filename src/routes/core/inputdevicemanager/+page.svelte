<script>
	import { Heading, P, A, Alert, Button, Hr, List, Li } from 'flowbite-svelte';

	import { CodeBlock } from 'svhighlight';
	import 'highlight.js/styles/base16/papercolor-dark.css';
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl"
	>Input Device Manager</Heading
>
<div class="p-4">
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Overview</Heading
	>
	<P class="mb-4">
		The InputDeviceManager is a static class that manages input devices, player inputs, and control
		schemes across the application. It provides centralized input management for both single-player
		and multiplayer scenarios.
	</P>
	<P class="mb-4">
		This manager handles <strong class="font-bold text-rose-400">player input registration</strong>,
		<strong class="font-bold text-rose-400">control scheme tracking</strong>, and
		<strong class="font-bold text-rose-400">action map management</strong> for loading states.
	</P>
	<Alert border>
		<div class="flex flex-row">
			<i class="fa-solid fa-circle-info fa-2xl mr-4 mt-4"></i>
			<div>
				<P
					>The InputDeviceManager is automatically used by <A
						class="font-bold text-sky-400"
						href="/luna/framework/uimanager">LunaUIManager</A
					> and doesn't require manual initialization in most cases.</P
				>
			</div>
		</div>
	</Alert>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Integration with Other Components</Heading
	>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>LunaUIManager Integration</Heading
	>
	<P class="mb-4">
		The InputDeviceManager is automatically initialized and managed by <A
			class="font-bold text-sky-400"
			href="/luna/framework/uimanager">LunaUIManager</A
		>. The LunaUIManager calls OnEnable() and OnDisable() methods and handles player input
		registration through its OnPlayerJoined and OnPlayerLeft events.
	</P>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>InputPrompt Integration</Heading
	>
	<P class="mb-4">
		<A class="font-bold text-sky-400" href="/luna/components/inputprompt">InputPrompt</A> components
		automatically subscribe to InputDeviceManager events to update their display when:
	</P>
	<List tag="ul" class="space-y-1 py-2">
		<Li>Control schemes change (OnControlSchemeChange event)</Li>
		<Li>Players join or leave (OnPlayerAdded/OnPlayerRemoved events)</Li>
		<Li>Input bindings are updated</Li>
	</List>

	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Properties</Heading
	>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>Player Inputs</Heading
	>
	<P class="mb-4">
		Collection of all registered PlayerInput instances. Used for managing multiple players in local
		multiplayer scenarios.
	</P>
	<CodeBlock
		language="csharp"
		code={`public static List<PlayerInput> PlayerInputs { get; }`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>Current Control Schemes</Heading
	>
	<P class="mb-4">
		List of current control schemes for each player. Tracks the active input method (keyboard,
		gamepad, etc.) for each registered player.
	</P>
	<CodeBlock
		language="csharp"
		code={`public static List<InputIconControlScheme> CurrentSchemes { get; }`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>Escape Action Names</Heading
	>
	<P class="mb-4">
		List of action names that trigger escape functionality. These actions are automatically bound to
		escape events when players are registered.
	</P>
	<CodeBlock
		language="csharp"
		code={`public static List<string> EscapeActionNames { get; }`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>Loading Action Maps</Heading
	>
	<P class="mb-4">
		List of action map names that should be enabled during loading states. These maps are
		automatically managed during loading transitions.
	</P>
	<CodeBlock
		language="csharp"
		code={`public static List<string> LoadingActionMaps { get; }`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>

	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Events</Heading
	>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>Player Events</Heading
	>
	<P class="mb-4">Events triggered when players are added or removed from the input system.</P>
	<CodeBlock
		language="csharp"
		code={`public static event Action<PlayerInput, int> OnPlayerAdded;
public static event Action<PlayerInput, int> OnPlayerRemoved;`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>Control Scheme Change</Heading
	>
	<P class="mb-4">
		Event triggered when a player's control scheme changes (e.g., switching from keyboard to
		gamepad).
	</P>
	<CodeBlock
		language="csharp"
		code={`public static event Action<InputIconControlScheme> OnControlSchemeChange;`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>

	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Initialization Methods</Heading
	>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>OnEnable</Heading
	>
	<P class="mb-4">
		Initializes the InputDeviceManager with escape action names, loading action maps, and
		multiplayer settings. Called automatically by LunaUIManager.
	</P>
	<CodeBlock
		language="csharp"
		code={`public static void OnEnable(List<string> escapeActionNames, List<string> loadingActionMaps, bool localMultiplayer)`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>OnDisable</Heading
	>
	<P class="mb-4">
		Cleans up the InputDeviceManager by unsubscribing from input system events. Called automatically
		when the manager is disabled.
	</P>
	<CodeBlock
		language="csharp"
		code={`public static void OnDisable()`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>

	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Player Management</Heading
	>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>AddPlayerInput</Heading
	>
	<P class="mb-4">
		Registers a new PlayerInput instance with the manager. Automatically binds escape actions and
		updates control scheme tracking.
	</P>
	<CodeBlock
		language="csharp"
		code={`public static void AddPlayerInput(PlayerInput playerInput)`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>RemovePlayerInput</Heading
	>
	<P class="mb-4">
		Unregisters a PlayerInput instance from the manager. Cleans up escape action bindings and
		removes from tracking lists.
	</P>
	<CodeBlock
		language="csharp"
		code={`public static void RemovePlayerInput(PlayerInput playerInput)`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>

	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Control Scheme Management</Heading
	>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>UpdateControlScheme</Heading
	>
	<P class="mb-4">
		Updates the control scheme for a specific player input index. Triggers the OnControlSchemeChange
		event if the scheme has changed.
	</P>
	<CodeBlock
		language="csharp"
		code={`public static void UpdateControlScheme(int inputIndex, bool forceInvoke = false)
// or
public static void UpdateControlScheme(InputIconControlScheme newScheme, int inputIndex, bool forceInvoke = false)`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>

	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Action Map Management</Heading
	>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>Loading State Methods</Heading
	>
	<P class="mb-4">
		Methods for managing action maps during loading states. These are called automatically by
		loading transitions.
	</P>
	<CodeBlock
		language="csharp"
		code={`public static void OnLoadingStart()
public static void OnLoadingEnd()`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>Action Map Control</Heading
	>
	<P class="mb-4">
		Utility methods for enabling and disabling specific action maps across input assets.
	</P>
	<CodeBlock
		language="csharp"
		code={`public static void SetEnabledActionMaps(InputActionAsset asset, ICollection<string> mapsToEnable)
public static void SetDisabledActionMaps(InputActionAsset asset, ICollection<string> mapsToDisable)
public static void ActionMapEnableOthers(InputActionAsset inputActionAsset, List<string> actionMapsToEnable)`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>

	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Usage Examples</Heading
	>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>Listening to Player Events</Heading
	>
	<P class="mb-4">
		Example of how to listen to player join/leave events for UI updates or game logic.
	</P>
	<CodeBlock
		language="csharp"
		code={`void Start()
{
    InputDeviceManager.OnPlayerAdded += OnPlayerJoined;
    InputDeviceManager.OnPlayerRemoved += OnPlayerLeft;
}

void OnPlayerJoined(PlayerInput playerInput, int playerIndex)
{
    Debug.Log($"Player {playerIndex} joined with device: {playerInput.devices[0].displayName}");
    // Update UI, spawn player, etc.
}

void OnPlayerLeft(PlayerInput playerInput, int playerIndex)
{
    Debug.Log($"Player {playerIndex} left");
    // Clean up player data, update UI, etc.
}`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>Control Scheme Changes</Heading
	>
	<P class="mb-4">Example of how to respond to control scheme changes for UI updates.</P>
	<CodeBlock
		language="csharp"
		code={`void Start()
{
    InputDeviceManager.OnControlSchemeChange += OnControlSchemeChanged;
}

void OnControlSchemeChanged(InputIconControlScheme newScheme)
{
    // Update input prompts, button icons, etc.
    switch (newScheme)
    {
        case InputIconControlScheme.Keyboard:
            // Show keyboard prompts
            break;
        case InputIconControlScheme.Gamepad:
            // Show gamepad prompts
            break;
    }
}`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Alert border>
		<div class="flex flex-row">
			<i class="fa-solid fa-circle-info fa-2xl mr-4 mt-4"></i>
			<div>
				<P
					>In most cases, you don't need to manually interact with InputDeviceManager. It's
					automatically managed by LunaUIManager and works seamlessly with the UI system.</P
				>
			</div>
		</div>
	</Alert>
</div>
