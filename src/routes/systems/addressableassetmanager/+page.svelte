<script>
	import { Heading, P, A, Mark, Secondary, GradientButton, Hr } from 'flowbite-svelte';

	import { CodeBlock } from 'svhighlight';
	import 'highlight.js/styles/base16/papercolor-dark.css';

	import prefabloader from '$lib/img/docs/core/prefabloader.jpg';
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl"
	>Systems/ Addressable Asset Manager</Heading
>
<div class="p-4">
	<P class="pb-4">The AddressableAssetManager is a utility class for managing Unity Addressable assets. It provides functionality to load, instantiate, and release Addressable assets efficiently while keeping track of instantiated game objects.</P>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>Public Methods</Heading
	>
	<CodeBlock
		language="csharp"
		code={`
/// <summary>
/// Loads an asset of type T from the given asset reference.
/// </summary>
/// <typeparam name="T">The type of asset to load.</typeparam>
/// <param name="assetReference">The asset reference to load the asset from.</param>
/// <returns>The loaded asset.</returns>
public static object LoadAsset<T>(AssetReference assetReference)

public static GameObject InstantiateSync(AssetReference assetReference, Vector3? position = null, Quaternion? rotation = null)

/// <summary>
/// Releases the handle and destroys all game objects associated with it.
/// </summary>
/// <param name="assetReference">The asset reference to release and destroy.</param>
/// <returns>True if the release and destruction was successful, false otherwise.</returns>
public static bool DestroyAllThenRelease(AssetReference assetReference)

public static bool ReportDestroy(AssetReference assetReference, GameObject instance)

/// <summary>
/// Checks if the specified asset reference is loaded.
/// </summary>
/// <param name="assetReference">The asset reference to check.</param>
/// <returns><c>true</c> if the asset reference is loaded; otherwise, <c>false</c>.</returns>
public static bool IsLoaded(AssetReference assetReference)

public static GameObject GetFirstInstance(AssetReference assetReference)

public static List<GameObject> GetInstances(AssetReference assetReference)

public static bool DestroyAllWithoutRelease(AssetReference assetReference)

/// <summary>
/// Destroys all instantiated game objects associated with the specified AsyncOperationHandle
/// and removes the handle from the dictionary.
/// </summary>
/// <param name="handle">The AsyncOperationHandle to destroy game objects for.</param>
public static void DestroyAllWithoutRelease(AsyncOperationHandle handle)

#if UNITASK_INSTALLED
/// <summary>
/// Loads an asset asynchronously from an AssetReference.
/// </summary>
/// <typeparam name="T">The type of asset to load.</typeparam>
/// <param name="assetReference">The AssetReference of the asset to load.</param>
/// <returns>A UniTask representing the asynchronous loading operation.</returns>
public static async UniTask<object> LoadAssetAsync<T>(AssetReference assetReference)

/// <summary>
/// Instantiates a GameObject asynchronously from an AssetReference.
/// </summary>
/// <param name="assetReference">The AssetReference of the GameObject to instantiate.</param>
/// <param name="position">The position of the instantiated GameObject. If null, the default position is Vector3.zero.</param>
/// <param name="rotation">The rotation of the instantiated GameObject. If null, the default rotation is Quaternion.identity.</param>
/// <returns>The instantiated GameObject.</returns>
public static async UniTask<GameObject> InstantiateAsync(AssetReference assetReference, Vector3? position = null, Quaternion? rotation = null)
#endif`}
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
public static event Action<AssetReference, GameObject> OnInstanceDestroy;
public static event Action<AssetReference> OnAssetUnloaded;`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
</div>
