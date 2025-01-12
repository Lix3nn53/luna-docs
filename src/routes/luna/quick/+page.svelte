<script>
  import { Heading, P, A, Mark, Secondary, GradientButton , Hr  } from 'flowbite-svelte';
	import samples from '$lib/img/docs/quick/samples.png';
  import window from '$lib/img/docs/quick/window.png';

  let hrClass = 'h-px my-8 bg-gray-200 border-0 dark:bg-gray-400';
</script>


<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl">Quick Start</Heading>
<div class="p-4">
  <Heading tag="h2" class="mb-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl">1 - Import Game Sample</Heading>
  <P class="mb-2">
    Start by importing one of the Game samples. 
    <strong class="font-extrabold text-rose-400">Demo Game</strong> or if you prefer addressables version, <strong class="font-extrabold text-rose-400">Demo Game Addressables</strong>.
  </P>
  <img alt="samples" src={samples} class="max-w-2xl mb-6 rounded-xl border-4"/>
  <Heading tag="h2" class="mb-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl">2 - Setup Game Sample</Heading>
  <P class="mb-0">Luna UI Panel should open. If it didn't, open it via <strong class="font-extrabold text-rose-400">Tools > Cupkek Games > Luna UI Panel</strong></P>
  <P class="mb-0">Complete setup by clicking buttons.</P>
  <P class="mb-0"><strong class="font-extrabold">Demo Game</strong> adds demo scenes to Build Settings.</P>
  <P class="mb-2"><strong class="font-extrabold">Demo Game Addressables</strong> makes demo scenes addressable.</P>
  <img alt="window" src={window} class="max-w-xs mb-6 rounded-xl border-4"/>
  <Heading tag="h2" class="mb-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl">3 - Ready!</Heading>
  <P class="mb-0">Go to <strong class="font-extrabold text-rose-400">Assets/Samples/LunaUI/</strong> to find demo folder.</P>
  <P class="mb-0">You can open and start the initialization scene.</P>
</div>