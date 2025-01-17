<script>
	import { Heading, P, A, Mark, Secondary, GradientButton, Hr, Li, List } from 'flowbite-svelte';
	import loading_transition from '$lib/img/docs/views/loading_transition.png';
	import loading from '$lib/img/docs/views/loading.jpg';

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
	let tdrowClass = 'border-stone-500';
	let tdClass = 'px-6 py-2 whitespace-normal font-medium bg-stone-700';
	let tdClasss = 'px-6 py-2 whitespace-normal font-medium bg-stone-600 min-w-48';
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl"
	>Views/ Loading</Heading
>
<div class="p-4">
	<img alt="loading" src={loading} class="mb-6 max-w-2xl rounded-xl border-4" />
	<P
		>The LoadingView is a simple component. It works alongside the SceneTransitionManager, which can
		be extended with custom transitions. You can refer to the demo game samples to see it in action.</P
	>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>SceneTransitionManager</Heading
	>
	<img
		alt="loading_transition"
		src={loading_transition}
		class="mb-6 max-w-md rounded-xl border-4"
	/>
	<P
		>Dictionary of transitions. Used by SceneLoader and SceneLoaderAddressable but you can also use
		it directly.</P
	>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>SceneTransition</Heading
	>
	<P>An abstract class you can implement add to SceneTransitionManager.</P>
	<CodeBlock
		language="csharp"
		code={`
public class SceneLoadTransitionFade : SceneTransition
{
	public float _fadeInDuration = 0.5f;
	public float _fadeOutDuration = 1f; // Longer because game lags when loading scene
	public override float GetStartDelay()
	{
		return _fadeInDuration + 0.2f; // add some duration to make sure fade is complete before scene loading starts
	}
	public override void FadeIn()
	{
		SceneTransition.LoadingScreenToggleEvent?.Invoke(true, _fadeInDuration);
	}

	public override void FadeOut()
	{
		SceneTransition.LoadingScreenToggleEvent?.Invoke(false, _fadeOutDuration);
	}
}`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>SceneTransition.LoadingScreenToggleEvent</Heading
	><P class="pb-4">This event is used to fade LoadingScreen.</P><Table class="rounded">
		<TableHead>
			<TableHeadCell class={tdheadClass}>Paramater</TableHeadCell>
			<TableHeadCell class={tdheadClass}>Type</TableHeadCell>
			<TableHeadCell class={tdheadClass}>Description</TableHeadCell>
		</TableHead>
		<TableBody tableBodyClass="divide-y">
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>First parameter</TableBodyCell>
				<TableBodyCell {tdClass}>bool</TableBodyCell>
				<TableBodyCell {tdClass}>True means fade-in, false means fade-out.</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>Second parameter</TableBodyCell>
				<TableBodyCell {tdClass}>float</TableBodyCell>
				<TableBodyCell {tdClass}>Duration of fade.</TableBodyCell>
			</TableBodyRow>
		</TableBody>
	</Table>
</div>
