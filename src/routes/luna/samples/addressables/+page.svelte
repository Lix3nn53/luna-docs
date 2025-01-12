<script>
  import { Heading, P, A, Mark, Secondary, GradientButton , Hr  } from 'flowbite-svelte';
	import samples from '$lib/img/docs/quick/samples.png';
  import window from '$lib/img/docs/quick/window.png';

  let hrClass = 'h-px my-8 bg-gray-200 border-0 dark:bg-gray-400';
</script>

<div class="p-4">
  <Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl">Sample/ Game Addressables</Heading>
  <div class="p-4">
    <P class="mb-2">
      A complete game demo featuring settings, save/load functionality, and a showcase of Luna UI's capabilities.
    </P>
    <P class="mb-2">
      Uses multi-scene workflow thanks to Addressables.
    </P>
    <P class="mb-2">
      Refer to <A color="text-blue-400" href="/luna/quick">quickstart</A> to get started.
    </P>
  </div>
</div>