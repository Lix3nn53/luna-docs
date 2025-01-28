<script>
	import { Heading, P, A, Mark, Secondary, GradientButton, AccordionItem, Accordion } from 'flowbite-svelte';
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl">Community & Support</Heading>
<div class="p-4">
	<Heading tag="h2" class="mb-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl">Discord</Heading>
	<P class="mb-6">Got questions or just want to hang out? Come join our Discord server! 🌟</P>
	<P class="mb-6">It's the best place to chat, connect, and get super-fast support from us and the community. We can't wait to see you there! 🎉</P>
	<GradientButton class="mb-4" color="cyanToBlue" href="https://discord.com/invite/k3yj8Az2VC" target="_blank">
		Join our community
		<i class="fa-brands fa-discord ms-2 flex items-center"></i>
	</GradientButton>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl">Mail</Heading>
	<P class="mb-6">We highly recommend using Discord over email, it's quicker and makes it easier to help you out!</P>
	<P class="mb-6">Before you send an email, pretty please check out the <A color="text-sky-400 font-extrabold" href="#faq">FAQ</A> and <A color="text-sky-400 font-extrabold" href="/luna/troubleshoot">Troubleshoot</A> sections first. Your answer might already be waiting for you there. If not, don't worry—reach out, and I'll be happy to assist!</P>
	<P class="mb-6"><span class="mr-2">Mail:</span><A color="text-sky-400 font-extrabold" href="mailto:cupkekgames@gmail.com" target="_blank">cupkekgames@gmail.com</A></P>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl" id="faq">Frequently Asked Questions</Heading>
	<Accordion multiple flush>
		<AccordionItem 
			tag="div"
			textFlushDefault="text-white"
			textFlushOpen="text-yellow-300 border-b-0 bg-stone-900"
			borderSharedClass="border-gray-200 dark:border-gray-50"
			borderBottomClass="border-b"
			paddingFlush="p-2"
		>
			<span slot="header">1 - TODO header</span>
			<div class="bg-stone-900 p-4">
				<p class="mb-2 ml-2 text-gray-50 dark:text-gray-50">todo text</p>
			</div>
		</AccordionItem>
		<AccordionItem 
			tag="div"
			textFlushDefault="text-white"
			textFlushOpen="text-yellow-300 border-b-0 bg-stone-900"
			borderSharedClass="border-gray-200 dark:border-gray-50"
			borderBottomClass="border-b"
			paddingFlush="p-2"
		>
			<span slot="header">2 - TODO header</span>
			<div class="bg-stone-900 p-4">
				<p class="mb-2 ml-2 text-gray-50 dark:text-gray-50">todo text</p>
			</div>
		</AccordionItem>
	</Accordion>
</div>
