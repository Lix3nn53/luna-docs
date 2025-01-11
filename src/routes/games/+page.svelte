<script>
  import { Heading, P, A, Mark, Secondary, GradientButton , Hr  } from 'flowbite-svelte';

  let hrClass = 'h-px my-8 bg-gray-200 border-0 dark:bg-gray-400';
</script>

<div class="p-2 lg:p-4 xl:p-8">
  <Heading tag="h1" class="mb-4" customSize="text-4xl font-extrabold  md:text-5xl lg:text-6xl">Games</Heading>
  <A class="mb-6" href="https://www.cupkek.games/">https://www.cupkek.games/</A>
  <div class="p-2 lg:p-4 xl:p-8">
    <Heading tag="h2" class="mb-4" customSize="text-2xl font-bold  md:text-3xl lg:text-4xl">Hero Manager</Heading>
    <P class="mb-6">Luna serves as the foundation for this UI-heavy game.</P>
    <iframe title="HeroManager" src="https://store.steampowered.com/widget/2671700/" frameborder="0" width="646" height="190"></iframe>
  </div>
</div>