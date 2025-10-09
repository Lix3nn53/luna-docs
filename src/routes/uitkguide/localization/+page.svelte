<script>
  import { Heading, P, A, Alert, Button, Hr, List, Li } from 'flowbite-svelte';

  import { CodeBlock } from 'svhighlight';
  import 'highlight.js/styles/base16/papercolor-dark.css';

  import step1 from '$lib/img/docs/uitk/localization/step1.jpg';
  import step2 from '$lib/img/docs/uitk/localization/step2.jpg';
  import step3 from '$lib/img/docs/uitk/localization/step3.jpg';
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl">Localization</Heading>
<div class="p-4">
  <P class="mb-4">
    Unity's localization package is integrated with UI Toolkit.
  </P>
  <P class="mb-4">
    Luna UI provides demos, guidelines, and utility functions for using Unity's Localization package.
  </P>
  <P class="mb-4">
    Check out the <A class="font-bold text-sky-400" href="/luna/samples/localization">Localization Sample</A>.
  </P>
  <Button outline  color="yellow" href="https://docs.unity3d.com/Packages/com.unity.localization@1.5/manual/UIToolkit.html" target="_blank">
    Unity Localization: UI Toolkit
    <i class="fa-solid fa-up-right-from-square ms-2 flex items-center"></i>
  </Button  >
  <div class="flex w-full items-center justify-center my-8">
    <iframe width="560" height="315" src="https://www.youtube.com/embed/TTimh8e3qVg?si=-UhT6f_gvmCpXxcO" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
  </div>
  <Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl">Guide</Heading>
  <Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2">UI Builder authoring</Heading>
  <P class="mb-4">You can use the UI Builder to create and fine-tune UI assets and their associated data bindings, including localization data bindings. You can connect to visual element attribute fields or styles. You can also address mismatched data types smoothly by creating your own converters for data type conversion.</P>
  <P class="mb-4">To bind an element's field to a localized value in UI Builder, do the following:</P>
  <List class="list-disc ml-8 mb-4">
    <Li>In the Inspector panel of an element, right-click on a field and select <strong>Add binding</strong>.</Li>
  </List>
  <img alt="Adding a binding through the UI Builder." src={step1} class="mb-6 xl:max-w-xl max-w-full rounded-xl border-4" />
  <List class="list-disc ml-8 mb-4">
    <Li>In the Add binding window, select the type of binding you want to use.</Li>
  </List>
  <img alt="Add binding window type popup showing localization binding types." src={step2} class="mb-6 xl:max-w-xl max-w-full rounded-xl border-4" />
  <List class="list-disc ml-8 mb-4">
    <Li>To set up the binding, specify the table and entry you want to reference. If you're using a LocalizedString binding and want to include local variables, you can do so through the Variables field.</Li>
  </List>
  <img alt="Configuring a localized string in the Add binding window." src={step3} class="mb-6 xl:max-w-xl max-w-full rounded-xl border-4" />
  <Alert class="mb-4" color="yellow">By default, the table and entry are referenced using the Guid and ID. To customize this behavior, go to <strong>Edit &gt; Preferences &gt; Localization</strong> and adjust the <strong>Table Reference Method</strong> and <strong>Entry Reference Method</strong> options.</Alert>
  <P class="mb-2">The UI builder-generated UXML includes the new localized string binding like this:</P>
  <CodeBlock
    language="xml"
    code={`
<ui:UXML xmlns:ui="UnityEngine.UIElements">
    <ui:Label text="Label">
        <Bindings>
            <UnityEngine.Localization.LocalizedString property="text" table="General Test Data" entry="My Entry">
                <variables>
                    <UnityEngine.Localization.LocalVariable name="counter">
                        <UnityEngine.Localization.SmartFormat.PersistentVariables.IntVariable value="2" />
                    </UnityEngine.Localization.LocalVariable>
                </variables>
            </UnityEngine.Localization.LocalizedString>
        </Bindings>
    </ui:Label>
</ui:UXML>`}
    showHeader={false}
    showLineNumbers={false}
    background="bg-zinc-900"
    headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
  />
</div>