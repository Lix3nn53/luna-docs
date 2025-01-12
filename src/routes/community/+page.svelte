<script>
  import { Heading, P, A, Mark, Secondary, GradientButton , Hr  } from 'flowbite-svelte';

  let hrClass = 'h-px my-8 bg-gray-200 border-0 dark:bg-gray-400';
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl">Community</Heading>
<div class="p-4">
  <Heading tag="h2" class="mb-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl">Discord</Heading>
  <P class="mb-6">If you have any questions or just want to chat, you can join our discord server.</P>
  <GradientButton color="purpleToBlue" href="https://discord.com/invite/k3yj8Az2VC" target="_blank">
    Join our community
    <i class="fa-brands fa-discord ms-2 flex items-center"></i>
  </GradientButton >
</div>