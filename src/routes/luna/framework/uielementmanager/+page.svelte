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

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl">UI Element Manager</Heading>
<div class="p-4">
  <P class="mb-4">
    Manages the registration and state of VisualElement instances within a hierarchy of VisualElement containers. 
    It provides functionality for <strong class="font-bold text-rose-400">enabling and disabling groups of elements</strong>, which is particularly useful for managing UI navigation. 
  </P>
  <P class="mb-4">
    Automatically adds <strong class="font-bold text-rose-400">audio feedback</strong> to interactable elements like buttons.
  </P>
  <P class="mb-4">
    Additionally, it includes functionality for setting a <strong class="font-bold text-rose-400">blocker element</strong>.
  </P>
  <Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl">Public Methods</Heading>
  <Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl">SetBlocker</Heading>
  <P>Disables all UI elements and sets a specified VisualElement as the active blocker, ensuring it remains enabled and interactive. When clicked, it will re-enable all previously disabled elements.</P>
  <CodeBlock
    language="csharp" 
    code={`
public void SetBlocker(VisualElement blocker)
// or
public void SetBlocker(string elementName)`}
    showHeader={false}
    showLineNumbers={false}
    background="bg-zinc-900"
    headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
  />
  <Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl">SetEnabledAll</Heading>
  <Alert border color="dark">
    <div class="flex flex-row">
      <i class="fa-solid fa-circle-info fa-2xl mt-4 mr-4"></i>
      <div>
        <P>The <A class="font-bold text-sky-400" href="/luna/framework/uiactions#UIViewActionEnableElements">UIViewActionEnableElements</A> uses these functions.</P>
      </div>
    </div>
  </Alert>
  <P></P>
  <CodeBlock
    language="csharp" 
    code={`
public List<VisualElement> SetEnabledAll(bool enabled, VisualElement except = null)
// or
public List<VisualElement> SetEnabledAll(bool enabled, List<VisualElement> except)`}
    showHeader={false}
    showLineNumbers={false}
    background="bg-zinc-900"
    headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
  />
  <Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl">SetEnabledPage</Heading>
  <P></P>
  <CodeBlock
    language="csharp" 
    code={`public void SetEnabledPage(VisualElement page, bool enabled)`}
    showHeader={false}
    showLineNumbers={false}
    background="bg-zinc-900"
    headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
  />
  <Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl">RegisterPage</Heading>
  <Alert border color="dark">
    <div class="flex flex-row">
      <i class="fa-solid fa-circle-info fa-2xl mt-4 mr-4"></i>
      <div>
        <P>You don't need to manually register elements when using UIViews.</P>
        <P>However, for documentation purposes, the functions are detailed here.</P>
      </div>
    </div>
  </Alert>
  <P></P>
  <CodeBlock
    language="csharp" 
    code={`public void RegisterPage(VisualElement parent)`}
    showHeader={false}
    showLineNumbers={false}
    background="bg-zinc-900"
    headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
  />
  <Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl">UnregisterPage</Heading>
  <P>Returns the predefined duration of fade transitions. Note that it does not reflect the current active transition duration.</P>
  <CodeBlock
    language="csharp" 
    code={`public void UnregisterPage(VisualElement parent)`}
    showHeader={false}
    showLineNumbers={false}
    background="bg-zinc-900"
    headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
  />
  <Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl">GetPage</Heading>
  <P></P>
  <CodeBlock
    language="csharp" 
    code={`public HashSet<VisualElement> GetPage(VisualElement parent)`}
    showHeader={false}
    showLineNumbers={false}
    background="bg-zinc-900"
    headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
  />
  <Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl">RegisterElement</Heading>
  <P></P>
  <CodeBlock
    language="csharp" 
    code={`public void RegisterElement(VisualElement parent, VisualElement item)`}
    showHeader={false}
    showLineNumbers={false}
    background="bg-zinc-900"
    headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
  />
  <Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl">UnregisterElement</Heading>
  <P></P>
  <CodeBlock
    language="csharp" 
    code={`public void UnregisterElement(VisualElement parent, VisualElement item)`}
    showHeader={false}
    showLineNumbers={false}
    background="bg-zinc-900"
    headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
  />
</div>