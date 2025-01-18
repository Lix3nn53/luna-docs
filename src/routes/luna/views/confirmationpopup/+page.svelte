<script>
	import { Heading, P, A, Mark, Secondary, GradientButton, Hr, Li, List } from 'flowbite-svelte';
	import confirmationpopup_ex from '$lib/img/docs/components/confirmationpopup_ex.png';
	import confirmationpopup_ins from '$lib/img/docs/components/confirmationpopup_ins.jpg';

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
	>Components/ Confirmation Popup</Heading
>
<div class="p-4">
	<img
		alt="confirmationpopup_ex"
		src={confirmationpopup_ex}
		class="mb-6 xl:max-w-xl max-w-full rounded-xl border-4"
	/>
	<P>Confirmation Popup is an UIView.</P>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Inspector</Heading
	>
	<img
		alt="confirmationpopup_ins"
		src={confirmationpopup_ins}
		class="mb-6 xl:max-w-xl max-w-full rounded-xl border-4"
	/>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Setup</Heading
	>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>1 - Create UXML with VisualElement that supports ConfirmationPopup</Heading
	>
	<P
		>You can use the template in the Game Library sample. Or you can create any custom VisualElement
		named "ConfirmationPopup" that has these VisualElement children:</P
	>
	<List tag="ul" class="space-y-1 py-2">
		<Li>Label with name "Header"</Li>
		<Li>Label with name "Body"</Li>
		<Li>Button with name "Accept"</Li>
		<Li>Button with name "Decline"</Li>
	</List>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>2 - Create UI Document and add Confirmation Popup</Heading
	>
	<P
		>Thats it, now you can reference and control ConfirmationPopup from your scripts and listen to
		OnAccept and OnDecline events.</P
	>
	<P
		>To control visibility of the ConfirmationPopup, use Fade just like how you control any other
		UIView.</P
	>
</div>
