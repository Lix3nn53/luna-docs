<script>
  import { Heading, P, A, Mark, Secondary, GradientButton, Hr  } from 'flowbite-svelte';

  let hrClass = 'h-px my-8 bg-gray-200 border-0 dark:bg-gray-400';
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl">Introduction</Heading>
<div class="p-4">
  <Heading tag="h2" class="mb-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl">Luna UI</Heading>
  <P class="mb-6">The Luna UI is built on top of Unity's UI Toolkit, offering simple solutions for common UI challenges without imposing any limitations on the UI Toolkit.</P>
  <GradientButton color="redToYellow" href="/luna/gallery">
    Learn more
    <i class="fa-solid fa-right-long ms-2 flex items-center"></i>
  </GradientButton>
  <Hr {hrClass} classHr="my-8" />
  <Heading tag="h2" class="mb-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl">Core Library</Heading>
  <P class="mb-6">The Core Library provides essential utilities, data structures, and base functionality to support scalable and efficient game development.</P>
</div>