<script>
  import { Heading, P, A, Alert, Button  , Hr  } from 'flowbite-svelte';

  import { CodeBlock } from 'svhighlight';
  import 'highlight.js/styles/base16/papercolor-dark.css';
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl">UI Navigation</Heading>
<div class="p-4">
  <P>Luna UI provides utilities to automatically disable unrelated interactable elements using the UIElementManager, enabling Unity's auto navigation to function without manual setup.</P>
  <Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl">Auto Navigation</Heading>
  <P class="mb-4">
    Each UI Toolkit panel features a focus ring that determines the focus order of elements. You can learn more about this feature here:
  </P>
  <Button outline  color="yellow" href="https://docs.unity3d.com/Manual/UIE-Events-Dispatching.html" target="_blank">
    Unity: Dispatch Events
    <i class="fa-solid fa-up-right-from-square ms-2 flex items-center"></i>
  </Button  >
  <P class="my-4">
    Luna UI provides an UI Action(<A class="font-bold text-sky-400" href="/luna/framework/uiactions#UIViewActionEnableElements">UIViewActionEnableElements</A>) to automatically disable unrelated interactable elements, enabling Unity's auto navigation to function without manual setup.
  </P>
  <Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl">Change what element is focused next</Heading>
  <P class="mb-4">
    You can manually determine what element is focused next.
  </P>
  <CodeBlock
  language="csharp" 
  code={`
myVisualElement.RegisterCallback<NavigationMoveEvent>(e =>
{
    switch(e.direction)
    {
        case NavigationMoveEvent.Direction.Up: U.Focus(); break;
        case NavigationMoveEvent.Direction.Down: D.Focus(); break;
        case NavigationMoveEvent.Direction.Left: L.Focus(); break;
        case NavigationMoveEvent.Direction.Right: R.Focus(); break;
    }
    e.PreventDefault();
});`}
  showHeader={true}
  showLineNumbers={true}
  background="bg-zinc-900"
  headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
/>
</div>