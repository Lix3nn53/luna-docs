<script>
	import {
		Heading,
		P,
		A,
		Mark,
		Secondary,
		GradientButton,
		Hr,
		Li,
		List,
		Button
	} from 'flowbite-svelte';

	import { CodeBlock } from 'svhighlight';
	import 'highlight.js/styles/base16/papercolor-dark.css';

	import overwatch from '$lib/img/docs/uitk/overwatch.mp4';
	import overwatchCell from '$lib/img/docs/uitk/overwatchCell.svg';
	import svgimport from '$lib/img/docs/uitk/svgimport.jpg';

	import {
		Table,
		TableBody,
		TableBodyCell,
		TableBodyRow,
		TableHead,
		TableHeadCell
	} from 'flowbite-svelte';

	let tdheadClass = 'px-6 py-4 whitespace-normal font-medium bg-stone-800 text-stone-50';
	let tdrowClass = 'border-stone-500';
	let tdClass = 'px-6 py-2 whitespace-normal font-medium bg-stone-700';
	let tdClasss = 'px-6 py-2 whitespace-normal font-medium bg-stone-600 min-w-48';
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl">
	UITK / Masking
</Heading>

<div class="p-4">
	<P>
		Masking is a technique used to control which portions of a UI element are visible.
		Within UI Toolkit, you can apply the USS property <code>overflow: hidden</code> to hide any parts of an element that extend beyond its parent.
	</P>

	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl">
		Unity Documentation
	</Heading>
	<P class="mb-4">
		Refer to the official Unity documentation.
	</P>
	<Button
		outline
		color="yellow"
		href="https://docs.unity3d.com/6000.0/Documentation/Manual/UIE-masking.html"
		target="_blank"
	>
		Unity Masking Documentation
		<i class="fa-solid fa-up-right-from-square ms-2 flex items-center"></i>
	</Button>

	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl">
		Overwatch-Style Progress Bar
	</Heading>
	<video
	class="mb-6 xl:max-w-xl max-w-full rounded-xl border-4"
	src={overwatch}
	controls
>
	<track kind="captions" />
	Your browser does not support HTML video.
</video>
	<P class="mb-4">
		This tutorial focuses solely on implementing the masking technique—not on creating the entire progress bar.
	</P>

	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2">
		1 - Install the Vector Package
	</Heading>
	<P class="mb-4">
		To enable masking with custom shapes, you’ll use SVG. To apply an SVG image as a background,
		you must <A color="text-sky-400 font-extrabold" href="https://docs.unity3d.com/6000.0/Documentation/Manual/upm-ui-actions.html" target="_blank">
			install the <code>com.unity.vectorgraphics</code> package
		</A>.
	</P>
	<P class="mb-4">
		The SVG background image will be applied to the parent element.
	</P>
	<P>
		Below is the SVG used in this example. Feel free to download and use it:
	</P>
	<img alt="overwatchCell" src={overwatchCell} class="mb-6 xl:max-w-xl max-w-full rounded-xl border-4" />
	<P>
		Import settings of the SVG:
	</P>
	<img alt="svgimport" src={svgimport} class="mb-6 xl:max-w-xl max-w-full rounded-xl border-4" />
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2">
		2 - Create the Visual Elements
	</Heading>
	<P>
		Let’s set up simple parent-child elements for the masking example:
	</P>
	<CodeBlock
		language="html"
		code={`
<engine:VisualElement class="progress-container">
	<engine:VisualElement class="progress-fill" />
</engine:VisualElement>`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>

	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2">
		3 - Style with Background-Repeat
	</Heading>
	<CodeBlock
		language="css"
		code={`
.progress-container {
  flex: 1;
  overflow: hidden;
	background-image: url('overwatchCell.svg');
  background-repeat: repeat-x;
  background-position-x: left 0px;
  background-position-y: top 0px;
  background-size: 20px 100%; /* Control the width and height; the width determines how many times the background image repeats. */
}

.progress-fill {
  height: 100%;
  width: 80%; /* Determines the fill amount */
}`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2">
		4 - Controlling Background with Script
	</Heading>
	<P>
		Use these functions to adjust the background image size, which in turn determines the number of repeats. And set the width of the fill element to control the fill amount.
	</P>
	<CodeBlock
		language="csharp"
		code={`
private void SetBackgroundImageWidth(int widthInPixels)
{
	// Update the background size of the progress container.
	// Set the width in pixels and the height to 100% of the container.
	_progressContainer.style.backgroundSize = new BackgroundSize(
		new Length(widthInPixels, LengthUnit.Pixel), 
		Length.Percent(100)
	);
}

public void SetBackgroundImageRepeatAmount(int repeatAmount)
{
	// Retrieve the current width of the progress container.
	float width = _progressContainer.contentRect.width;
	
	// Ensure the width is valid (not NaN and greater than zero).
	// The contentRect is not calculated at first frames, so be careful.
	// You might have to manually call SetBackgroundImageWidth if you need to set the width at the start.
	if (float.IsNaN(width) || width <= 0)
	{
		return;
	}

	// Calculate the width for a single background cell, rounding to the nearest pixel.
	int cellWidth = (int)(width / repeatAmount + 0.5f);

	// Apply the calculated cell width to update the background image size.
	SetBackgroundImageWidth(cellWidth);
}

public void SetFillAmount(float fillAmount)
{
	// Make sure fillAmount is within the range [0, 1].
	fillAmount = Mathf.Clamp01(fillAmount);
	// Update the width of the fill element.
	_progressFill.style.width = Length.Percent(fillAmount * 100);
}
	`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	
</div>
