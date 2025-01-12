<script>
  import { Heading, P, A, Mark, Secondary, Button  , Hr  } from 'flowbite-svelte';
  import { Table, TableBody, TableBodyCell, TableBodyRow, TableHead, TableHeadCell } from 'flowbite-svelte';
	import unity from '$lib/img/docs/whyuitk/unity.png';

  let tdheadClass = 'px-6 py-4 whitespace-normal font-medium bg-stone-800 text-stone-50';
  let tdrowClass = 'border-stone-200';
  let tdClass = 'px-6 py-4 whitespace-normal font-medium bg-stone-700';
  let tdClasss = 'px-6 py-4 whitespace-normal font-medium bg-stone-800';
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl">Why UI Toolkit?</Heading>
<div class="p-4">
  <P class="mb-4">
    <span>In summary, </span> <strong class="font-bold">Unity UI (uGUI)</strong> <span> is ideal if you prioritize familiarity or require 
    3D elements and custom shaders. </span> <strong class="font-bold"> UI Toolkit</strong> <span> is the better choice if you need scalable, 
    high-performance layouts with modern styling options.</span>
  </P>
  <Heading tag="h2" class="mb-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl">Unity's comparison</Heading>
  <img src={unity} alt="unity" class="mb-6"/>
  <Button outline  color="yellow" href="https://docs.unity3d.com/Manual/UI-system-compare.html" target="_blank">
    Unity's Comparison
    <i class="fa-solid fa-up-right-from-square ms-2 flex items-center"></i>
  </Button  >
  <Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl">Comparison</Heading>
  <Table class="border-4 border-stone-400 rounded">
    <TableHead>
      <TableHeadCell class={tdheadClass}>Subject</TableHeadCell>
      <TableHeadCell class={tdheadClass}>Unity UI (uGUI)</TableHeadCell>
      <TableHeadCell class={tdheadClass}>UI Toolkit</TableHeadCell>
    </TableHead>
    <TableBody tableBodyClass="divide-y">
      <TableBodyRow color="custom" class={tdrowClass}>
        <TableBodyCell {tdClass}>Architecture</TableBodyCell>
        <TableBodyCell {tdClass}>GameObject-based, with each UI element as a GameObject and Component</TableBodyCell>
        <TableBodyCell {tdClass}>DOM-like visual tree (similar to web) with no GameObject overhead</TableBodyCell>
      </TableBodyRow>
      <TableBodyRow color="custom" class={tdrowClass}>
        <TableBodyCell tdClass={tdClasss}>Scalability</TableBodyCell>
        <TableBodyCell tdClass={tdClasss}>Prefabs provide reusable UI elements but can become cumbersome to manage, especially with complex nested hierarchies and style adjustments</TableBodyCell>
        <TableBodyCell tdClass={tdClasss}>UXML and USS enable reusable, modular UI components with styles applied globally, making it easier to manage and update UI elements consistently across the project</TableBodyCell>
      </TableBodyRow>
      <TableBodyRow color="custom" class={tdrowClass}>
        <TableBodyCell {tdClass}>Performance</TableBodyCell>
        <TableBodyCell {tdClass}>Higher overhead with many UI elements, due to GameObjects and RectTransforms</TableBodyCell>
        <TableBodyCell {tdClass}>More efficient due to lightweight visual elements and optimized rendering</TableBodyCell>
      </TableBodyRow>
      <TableBodyRow color="custom" class={tdrowClass}>
        <TableBodyCell tdClass={tdClasss}>Layout System</TableBodyCell>
        <TableBodyCell tdClass={tdClasss}>Uses RectTransforms and anchors, which can be tricky for responsive layouts</TableBodyCell>
        <TableBodyCell tdClass={tdClasss}>Flexbox layout, more intuitive and powerful for dynamic, responsive UIs</TableBodyCell>
      </TableBodyRow>
      <TableBodyRow color="custom" class={tdrowClass}>
        <TableBodyCell {tdClass}>Styling</TableBodyCell>
        <TableBodyCell {tdClass}>Customization done through scripting and component adjustments</TableBodyCell>
        <TableBodyCell {tdClass}>USS (similar to CSS), allowing for powerful and reusable styling</TableBodyCell>
      </TableBodyRow>
      <TableBodyRow color="custom" class={tdrowClass}>
        <TableBodyCell tdClass={tdClasss}>Ease of Use</TableBodyCell>
        <TableBodyCell tdClass={tdClasss}>Familiar GameObject workflow</TableBodyCell>
        <TableBodyCell tdClass={tdClasss}>Declarative UI (UXML/USS) more complex but promotes cleaner separation between logic and style</TableBodyCell>
      </TableBodyRow>
      <TableBodyRow color="custom" class={tdrowClass}>
        <TableBodyCell {tdClass}>Editor Experience</TableBodyCell>
        <TableBodyCell {tdClass}>Visible and manipulable directly in the Scene view</TableBodyCell>
        <TableBodyCell {tdClass}>Integrated tool called UI Builder</TableBodyCell>
      </TableBodyRow>
      <TableBodyRow color="custom" class={tdrowClass}>
        <TableBodyCell tdClass={tdClasss}>Textureless UI</TableBodyCell>
        <TableBodyCell tdClass={tdClasss}>No</TableBodyCell>
        <TableBodyCell tdClass={tdClasss}>Create visually appealing UI without relying on textures</TableBodyCell>
      </TableBodyRow>
      <TableBodyRow color="custom" class={tdrowClass}>
        <TableBodyCell {tdClass}>UI positioned and lit in a 3D world</TableBodyCell>
        <TableBodyCell {tdClass}>Yes</TableBodyCell>
        <TableBodyCell {tdClass}>Possible to via render textures, but cumbersome to work with. (This feature is currently in progress.)</TableBodyCell>
      </TableBodyRow>
      <TableBodyRow color="custom" class={tdrowClass}>
        <TableBodyCell tdClass={tdClasss}>VFX with custom shaders and materials</TableBodyCell>
        <TableBodyCell tdClass={tdClasss}>Yes</TableBodyCell>
        <TableBodyCell tdClass={tdClasss}>No</TableBodyCell>
      </TableBodyRow>
    </TableBody>
  </Table>
</div>


