<script>
  import { Heading, P, A, Mark, Gallery, GradientButton , Hr  } from 'flowbite-svelte';
  import { Carousel, Thumbnails, Button, Indicator } from 'flowbite-svelte';
	import banner from '$lib/img/docs/gallery/banner_2.jpg';
	import panel from '$lib/img/docs/gallery/luna_panel.jpg';
	import panel2 from '$lib/img/docs/gallery/luna_panel_2.jpg';
	import panel3 from '$lib/img/docs/gallery/luna_panel_3.jpg';
	import demos from '$lib/img/docs/gallery/luna_demos.jpg';
	import input from '$lib/img/docs/gallery/luna_input.jpg';
	import inventory from '$lib/img/docs/gallery/luna_inventory.jpg';
	import dialogue from '$lib/img/docs/gallery/dialogue.jpg';
	import buttons from '$lib/img/docs/gallery/luna_buttons.png';
	import progress_bars from '$lib/img/docs/gallery/luna_progress_bars.jpg';
	import tabview from '$lib/img/docs/gallery/luna_tabview.jpg';
	import tooltip from '$lib/img/docs/gallery/luna_tooltip.jpg';
	import collections from '$lib/img/docs/gallery/luna_collections.jpg';
	import popup from '$lib/img/docs/gallery/luna_confirmationpopup.jpg';

  export const images = [
    {
      alt: 'Banner',
      src: banner,
      title: 'Banner'
    },
    {
      alt: 'panel',
      src: panel,
      title: 'panel'
    },
    {
      alt: 'panel2',
      src: panel2,
      title: 'panel2'
    },
    {
      alt: 'panel3',
      src: panel3,
      title: 'panel3'
    },
    {
      alt: 'demos',
      src: demos,
      title: 'demos'
    },
    {
      alt: 'input',
      src: input,
      title: 'input'
    },
    {
      alt: 'inventory',
      src: inventory,
      title: 'inventory'
    },
    {
      alt: 'dialogue',
      src: dialogue,
      title: 'dialogue'
    },
    {
      alt: 'buttons',
      src: buttons,
      title: 'buttons'
    },
    {
      alt: 'progress_bars',
      src: progress_bars,
      title: 'progress_bars'
    },
    {
      alt: 'tabview',
      src: tabview,
      title: 'tabview'
    },
    {
      alt: 'tooltip',
      src: tooltip,
      title: 'tooltip'
    },
    {
      alt: 'collections',
      src: collections,
      title: 'collections'
    },
    {
      alt: 'popup',
      src: popup,
      title: 'popup'
    },
  ];

  let index = 0;
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl">Gallery</Heading>
<div class="p-2 lg:p-4 xl:p-8 h-full">
  <div class="space-y-4 h-full">
    <Carousel {images} class="min-h-96 h-96" imgClass="object-contain h-full w-fit" slideDuration={800} let:Indicators let:Controls bind:index>
      <Controls />
    </Carousel>
    <Thumbnails class="bg-transparent gap-2" let:Thumbnail let:image let:selected {images} bind:index>
      <Thumbnail {...image} {selected} class="rounded shadow-xl hover:outline hover:outline-primary-500" activeClass="outline outline-primary-400"/>
    </Thumbnails>
  </div>
</div>