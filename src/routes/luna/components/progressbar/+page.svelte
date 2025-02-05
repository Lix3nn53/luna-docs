<script>
	import { Heading, P, A, Alert, Secondary, GradientButton, Hr, Li, List } from 'flowbite-svelte';
	import progressbar from '$lib/img/docs/components/progressbar.png';
	import progressbar2 from '$lib/img/docs/components/progressbar2.png';
	import progress_bars from '$lib/img/docs/gallery/luna_progress_bars.jpg';

	import { CodeBlock } from 'svhighlight';
	import 'highlight.js/styles/base16/papercolor-dark.css';

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

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl"
	>Components/ Progress Bar</Heading
>
<div class="p-4">
	<img alt="samples" src={progress_bars} class="mb-6 xl:max-w-xl max-w-full rounded-xl border-4" />
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Attributes</Heading
	>
	<img alt="progressbar" src={progressbar} class="mb-6 max-w-md rounded-xl border-4" />
	<img alt="progressbar2" src={progressbar2} class="mb-6 max-w-md rounded-xl border-4" />
	<Table class="rounded">
		<TableHead>
			<TableHeadCell class={tdheadClass}>Attribute</TableHeadCell>
			<TableHeadCell class={tdheadClass}>Description</TableHeadCell>
		</TableHead>
		<TableBody tableBodyClass="divide-y">
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdheadClass}>Progress Settings</TableBodyCell>
				<TableBodyCell tdClass={tdheadClass}
					>Progress Settings</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>Instant Positive</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}
					>If value increased Progress and Indicator changes will be shown instantly.</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>Instant Negative</TableBodyCell>
				<TableBodyCell {tdClass}
					>If value negative Progress and Indicator changes will be shown instantly.</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>Update Frequency</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}>interval in ms</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>Step</TableBodyCell>
				<TableBodyCell {tdClass}>How much length progress bar moves per update.</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>First Delay</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}
					>Delay before the first bar starts to move. First bar can be main bar or indicator bar,
					depending on the change. If change is negative, main bar moves first followed by indicator
					bar. If change in positive, indicator bar moves first followed by main bar.</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>Second Delay</TableBodyCell>
				<TableBodyCell {tdClass}
					>Delay before the second bar starts to move. First bar can be main bar or indicator bar,
					depending on the change. If change is negative, main bar moves first followed by indicator
					bar. If change in positive, indicator bar moves first followed by main bar.</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>Progress</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}
					>Multiple progress fills.</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>Indicator</TableBodyCell>
				<TableBodyCell {tdClass}
					>Indicator fill, hidden under the progress fills.</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdheadClass}>Color Settings</TableBodyCell>
				<TableBodyCell tdClass={tdheadClass}
					>Color Settings</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>Color Background</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}>Background color.</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>Color Indicator Positive</TableBodyCell>
				<TableBodyCell {tdClass}
					>Color of the indicator bar when the change is positive.</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>Color Indicator Negative</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}
					>Color of the indicator bar when the change is negative.</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdheadClass}>Other Settings</TableBodyCell>
				<TableBodyCell tdClass={tdheadClass}
					>Other Settings</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>Title</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}>Text to display on the bar.</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>Show Icon</TableBodyCell>
				<TableBodyCell {tdClass}>Show icon on left of the ProgressBar.</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>Icon Size</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}>Width and height of the icon.</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>Icon Tint</TableBodyCell>
				<TableBodyCell {tdClass}>Image tint for the icon.</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>Vertical Line</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}
					>Make progress bar vertical instead of horizontal.</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdheadClass}>Overlay Settings</TableBodyCell>
				<TableBodyCell tdClass={tdheadClass}
					>Overlay Settings</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>Overlay Image</TableBodyCell>
				<TableBodyCell {tdClass}
					>Image to use for overlay. Use SVG if you need masking.</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>Overlay Image Width</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}
					>Width of the overlay image. Determines how many times it is repeated.</TableBodyCell
				>
			</TableBodyRow>
		</TableBody>
	</Table>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Progress Attributes</Heading
	>
	<Table class="rounded">
	<TableHead>
		<TableHeadCell class={tdheadClass}>Attribute</TableHeadCell>
		<TableHeadCell class={tdheadClass}>Description</TableHeadCell>
	</TableHead>
	<TableBody tableBodyClass="divide-y">
		<TableBodyRow color="custom" class={tdrowClass}>
			<TableBodyCell {tdClass}>CurrentValue</TableBodyCell>
			<TableBodyCell {tdClass}
				>Clamp between 0-1. Current fill value. You don't wanna edit this directly.</TableBodyCell
			>
		</TableBodyRow>
		<TableBodyRow color="custom" class={tdrowClass}>
			<TableBodyCell tdClass={tdClasss}>TargetValue</TableBodyCell>
			<TableBodyCell tdClass={tdClasss}
				>Clamp between 0 and 1. This is the target fill value. <br/>Modify this to change the fill level, but simply editing it is not enough—you must also trigger an update. <br/>See the example below.</TableBodyCell
			>
		</TableBodyRow>
		<TableBodyRow color="custom" class={tdrowClass}>
			<TableBodyCell {tdClass}>Color</TableBodyCell>
			<TableBodyCell {tdClass}
				>Color of the progress bar.</TableBodyCell
			>
		</TableBodyRow>
		</TableBody>
	</Table>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Public Methods</Heading
	>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>RebuildProgressSegments</Heading
	>
	<P>Must be called if you change Length of Progress array. Creates or removes progress bars.</P>
	<CodeBlock
		language="csharp"
		code={`public void RebuildProgressSegments()`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>UpdateProgressSegments</Heading
	>
	<P>Call this to apply the new TargetValue changes made to elements in the Progress array.</P>
	<CodeBlock
		language="csharp"
		code={`public void UpdateProgressSegments()`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>PlayProgress</Heading
	>
	<P>Call to visually apply the values of Progress array.</P>
	<CodeBlock
		language="csharp"
		code={`public void PlayProgress()`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>PlayIndicator</Heading
	>
	<P>Call to visually apply the value of Indicator.</P>
	<CodeBlock
		language="csharp"
		code={`public void PlayIndicator()`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>SetIndicatorStyle</Heading
	>
	<P>This is handled automatically. But if you want, you can change the style of indicator fill manually.</P>
	<CodeBlock
		language="csharp"
		code={`public void SetIndicatorStyle(bool positive)`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>SetFilling</Heading
	>
	<P>There must be only one element in Progress array.</P>
	<P>Useful for when you wanna highlight a change.</P>
	<CodeBlock
		language="csharp"
		code={`
public void SetFilling(float current, float add, float max)

// Example:
// Suppose you have an Experience Bar and want to highlight gained EXP.
// You can call it as shown below to display both the current and gained values simultaneously.
experienceBar.SetFilling(currentExp, add, expRequiredForNextLevel);
`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>SetOverlayRepeatAmount</Heading
	>
	<P>The repeat amount of overlay image is controlled by OverlayImageWidth.</P>
	<p>This function calculates and sets OverlayImageWidth based on the given repeatAmount and contentRect.width of the ProgressBar.</p>
	<Alert border color="yellow">
		<div class="flex flex-row">
			<i class="fa-solid fa-circle-info fa-2xl mr-4 mt-4"></i>
			<div>
				<P class="mb-4"
					>Warning: contentRect.width is not calculated during the initial frames. This function will only work after the first few frames.</P
				>
			</div>
		</div>
	</Alert>
	<CodeBlock
		language="csharp"
		code={`public void SetOverlayRepeatAmount(int repeatAmount)`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Example</Heading
	>
	<CodeBlock
		language="csharp"
		code={`
using UnityEngine;
using UnityEngine.UIElements;

namespace CupkekGames.Luna.Demo.Components
{
  public class ProgressBarDemo : MonoBehaviour
  {
    private UIDocument _uiDocument;
    private ProgressBar _progressBar;
    private Button _buttonDamage;
    private Button _buttonHeal;

    private void Awake()
    {
      _uiDocument = GetComponent<UIDocument>();

      _progressBar = _uiDocument.rootVisualElement.Q<ProgressBar>();

      _buttonDamage = _uiDocument.rootVisualElement.Q<Button>("Damage");
      _buttonHeal = _uiDocument.rootVisualElement.Q<Button>("Heal");
    }

    private void Start()
    {
      // Set instant to true to avoid animation at start
      _progressBar.InstantPositive = true;
      _progressBar.InstantNegative = true;

      _progressBar.Indicator.TargetValue = 1;
      _progressBar.PlayIndicator(); // You must call PlayIndicator to visually apply the value

      _progressBar.Progress[0].TargetValue = 1f;
      // Must be called after modifying the size of the Progress array. Not needed here, included for documentation purposes.
      _progressBar.RebuildProgressSegments(); 
      _progressBar.PlayProgress();  // You must call PlayIndicator to visually apply the value

      // Set instant back to false to play animation
      _progressBar.InstantPositive = false;
      _progressBar.InstantNegative = false;
    }

    private void OnEnable()
    {
      _buttonDamage.clicked += Damage;
      _buttonHeal.clicked += Heal;
    }

    private void OnDisable()
    {
      _buttonDamage.clicked -= Damage;
      _buttonHeal.clicked -= Heal;
    }

    private void Damage()
    {
      _progressBar.Progress[0].TargetValue -= 0.1f;
      _progressBar.Indicator.TargetValue = _progressBar.Progress[0].TargetValue;

      UpdateProgressBar();
    }

    private void Heal()
    {
      _progressBar.Progress[0].TargetValue += 0.1f;
      _progressBar.Indicator.TargetValue = _progressBar.Progress[0].TargetValue;

      UpdateProgressBar();
    }

    private void UpdateProgressBar()
    {
      // After updating, do NOT call RebuildProgressSegments. Instead, call UpdateProgressSegments.
      _progressBar.UpdateProgressSegments(); 
      _progressBar.PlayProgress(); // Visually apply the value of progress bars

      _progressBar.PlayIndicator(); // Visually apply the value of the indicator bar
    }
  }
}`}
		showHeader={true}
		showLineNumbers={true}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
</div>
