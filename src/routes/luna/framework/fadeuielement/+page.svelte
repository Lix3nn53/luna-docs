<script>
  import { Heading, P, A, Alert, Button  , Hr  } from 'flowbite-svelte';

  import { CodeBlock } from 'svhighlight';
  import 'highlight.js/styles/base16/papercolor-dark.css';

  import { Table, TableBody, TableBodyCell, TableBodyRow, TableHead, TableHeadCell } from 'flowbite-svelte';

  let tdheadClass = 'px-6 py-4 whitespace-normal font-medium bg-stone-800 text-stone-50';
  let tdrowClass = 'border-stone-200';
  let tdClass = 'px-6 py-4 whitespace-normal font-medium bg-stone-700';
  let tdClasss = 'px-6 py-4 whitespace-normal font-medium bg-stone-800';

  let code = `
public FadeUIElement(
  MonoBehaviour coroutineRunner, 
  VisualElement visualElement, 
  EasingMode easingMode = EasingMode.EaseOutCirc, 
  bool debug = false)`;
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl">FadeUIElement</Heading>
<div class="p-4">
  <P class="mb-4">
    The FadeUIElement class manages the fading in and out of a VisualElement.
  </P>
  <Alert border color="dark">
    <div class="flex flex-row">
      <i class="fa-solid fa-circle-info fa-2xl mt-4 mr-4"></i>
      <div>
        <P class="mb-4">When fading a <strong class="font-bold">UIView</strong>, always use the public <strong class="font-bold">Fade</strong> variable provided by the UIView to ensure <strong class="font-bold">Actions</strong> work correctly. 
          Typically, you should use this Fade rather than creating a custom instance.</P>
        <P>Only create a <strong class="font-bold">custom Fade</strong> instance if you need to fade a <strong class="font-bold"></strong>VisualElement <strong class="font-bold">independently of UIView</strong>.</P>
      </div>
    </div>
  </Alert>
  <Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl">Constructor</Heading>
  <CodeBlock
    language="csharp" 
    {code}
    showHeader={true}
    showLineNumbers={true}
    background="bg-zinc-900"
    headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
  />
  <Table class="border-4 border-stone-400 rounded my-4">
    <TableHead>
      <TableHeadCell class={tdheadClass}>Name</TableHeadCell>
      <TableHeadCell class={tdheadClass}>Type</TableHeadCell>
      <TableHeadCell class={tdheadClass}>Description</TableHeadCell>
    </TableHead>
    <TableBody tableBodyClass="divide-y">
      <TableBodyRow color="custom" class={tdrowClass}>
        <TableBodyCell {tdClass}>coroutineRunner</TableBodyCell>
        <TableBodyCell {tdClass}>MonoBehaviour</TableBodyCell>
        <TableBodyCell {tdClass}>MonoBehaviour that handles running coroutines.</TableBodyCell>
      </TableBodyRow>
      <TableBodyRow color="custom" class={tdrowClass}>
        <TableBodyCell tdClass={tdClasss}>visualElement</TableBodyCell>
        <TableBodyCell tdClass={tdClasss}>VisualElement</TableBodyCell>
        <TableBodyCell tdClass={tdClasss}>The VisualElement to be faded.</TableBodyCell>
      </TableBodyRow>
      <TableBodyRow color="custom" class={tdrowClass}>
        <TableBodyCell {tdClass}>easingMode</TableBodyCell>
        <TableBodyCell {tdClass}>EasingMode</TableBodyCell>
        <TableBodyCell {tdClass}>Defines the easing effect applied during fade transitions.</TableBodyCell>
      </TableBodyRow>
      <TableBodyRow color="custom" class={tdrowClass}>
        <TableBodyCell tdClass={tdClasss}>debug</TableBodyCell>
        <TableBodyCell tdClass={tdClasss}>bool</TableBodyCell>
        <TableBodyCell tdClass={tdClasss}>Logs fade transitions.</TableBodyCell>
      </TableBodyRow>
    </TableBody>
  </Table>
  <Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl">Public Methods</Heading>
  <Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl">FadeIn</Heading>
  <P></P>
  <CodeBlock
    language="csharp" 
    code={`public void FadeIn()`}
    showHeader={true}
    showLineNumbers={true}
    background="bg-zinc-900"
    headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
  />
  <Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl">FadeOut</Heading>
  <P></P>
  <CodeBlock
    language="csharp" 
    code={`public void FadeOut()`}
    showHeader={true}
    showLineNumbers={true}
    background="bg-zinc-900"
    headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
  />
  <Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl">SetDuration</Heading>
  <P></P>
  <CodeBlock
    language="csharp" 
    code={`public void SetDuration(float seconds)`}
    showHeader={true}
    showLineNumbers={true}
    background="bg-zinc-900"
    headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
  />
  <Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl">GetDuration</Heading>
  <P>Returns the predefined duration of fade transitions. Note that it does not reflect the current active transition duration.</P>
  <CodeBlock
    language="csharp" 
    code={`public float GetDuration()`}
    showHeader={true}
    showLineNumbers={true}
    background="bg-zinc-900"
    headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
  />
  <Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl">SetEasing</Heading>
  <P></P>
  <CodeBlock
    language="csharp" 
    code={`public void SetEasing(EasingMode easingMode)`}
    showHeader={true}
    showLineNumbers={true}
    background="bg-zinc-900"
    headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
  />
  <Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl">Stop</Heading>
  <P></P>
  <CodeBlock
    language="csharp" 
    code={`public void Stop()`}
    showHeader={true}
    showLineNumbers={true}
    background="bg-zinc-900"
    headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
  />
</div>