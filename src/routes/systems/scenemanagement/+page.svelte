<script>
	import { Heading, P, A, Mark, Secondary, GradientButton, Hr } from 'flowbite-svelte';

	import { CodeBlock } from 'svhighlight';
	import 'highlight.js/styles/base16/papercolor-dark.css';

	import prefabloader from '$lib/img/docs/core/prefabloader.jpg';
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl"
	>Systems/ Scene Management</Heading
>
<div class="p-4">
	<P class="pb-4">Simple scene loader for default single scene workflow.</P>
	<P class="pb-4">Powerful multi-scene manager for addressable scenes.</P>
	<Heading tag="h2" class="mb-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>SceneLoader</Heading
	>
	Singleton scene loader for default single scene workflow.
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>Public Methods</Heading
	>
	<CodeBlock
		language="csharp"
		code={`
public void LoadScene(string sceneName, SceneTransition sceneLoadTransition)
public void LoadScene(int sceneIndex, SceneTransition sceneLoadTransition)
public bool IsLoaded(string sceneName)
public bool IsLoaded(int sceneIndex)`}
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
		code={`
public event Action<string, int> OnSceneLoad; // Scene name and index`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h2" class="mb-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>SceneLoaderAddressable</Heading
	>
	Singleton scene loader for addressable scenes. Supports multiple scene loading and unloading at a single request.
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>Public Fields</Heading
	>
	<CodeBlock
		language="csharp"
		code={`
public List<SceneSO> LoadedScenes; // For debug puposes only, visible in editor, do not edit.`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>Public Methods</Heading
	>
	<CodeBlock
		language="csharp"
		code={`
public void LoadSceneRequest(List<SceneSO> scenesToLoad, List<SceneSO> scenesToUNNLoad, SceneTransition sceneLoadTransitionType)
public void LoadScene(List<SceneSO> scenesToLoad, SceneTransition sceneLoadTransitionType)
public void LoadScene(SceneSO sceneToLoad, SceneTransition sceneLoadTransitionType)
public void LoadScene(SceneSO sceneToLoad)
public void UnLoadScene(List<SceneSO> scenesToUNNLoad, SceneTransition sceneLoadTransitionType)
public void UnLoadScene(SceneSO scenesToUNNLoad, SceneTransition sceneLoadTransitionType)
public void UnLoadScene(SceneSO scenesToUNNLoad)
public void LoadSceneAndUnLoadCurrent(SceneSO sceneToLoad, SceneTransition sceneLoadTransitionType)
public void LoadSceneAndUnLoadCurrent(List<SceneSO> scenesToLoad, SceneTransition sceneLoadTransitionType)
public void UnloadAllCurrent(SceneTransition sceneLoadTransitionType)
public void SetActiveScene(SceneSO scene)
public bool IsLoaded(SceneSO gameSceneSO)`}
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
		code={`
public static Action<List<SceneSO>> SceneReadyEvent;
public static Action<List<SceneSO>> SceneUnloadEvent;`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
</div>
