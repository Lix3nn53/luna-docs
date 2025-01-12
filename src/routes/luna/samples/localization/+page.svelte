<script>
  import { Heading, P, A, Mark, Secondary, GradientButton , Hr  } from 'flowbite-svelte';
	import CreateLocalizationSettings from '$lib/img/docs/quick/CreateLocalizationSettings.png';
  import window from '$lib/img/docs/quick/window.png';

  let hrClass = 'h-px my-8 bg-gray-200 border-0 dark:bg-gray-400';
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl">Sample/ Localization</Heading>
<div class="p-4">
  <P class="mb-2">
    Unity's Localization package is integrated with UI Toolkit. Luna UI provides demos, guidelines, and utility functions for using Unity's Localization package.
  </P>
  <P class="mb-2">
    Don't forget to set the active localization settings.
  </P>
  <img alt="samples" src={CreateLocalizationSettings} class="max-w-2xl mb-6 rounded-xl border-4"/>
  <P class="mb-2">
    Refer to <A color="text-sky-400 font-extrabold" href="/luna/framework/localization">localization</A> for more info.
  </P>
</div>