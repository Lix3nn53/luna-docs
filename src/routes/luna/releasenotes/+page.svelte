<script>
  import { Heading, P, A, Mark, Gallery, GradientButton , Hr  } from 'flowbite-svelte';
  import { Carousel, Thumbnails, Button, Indicator } from 'flowbite-svelte';
	
</script>
<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl">Luna/ Release Notes</Heading>

<div class="p-2 lg:p-4 xl:p-8 h-full">
<pre class="whitespace-pre-wrap">
[1.0.3]
New:
- ProgressBar: Added an overlay feature. The API has changed significantly, and the documentation has been updated with new examples. Includes a new Overwatch-style health bar sample!
- PieChart: Made gap line strokes straight.
- ProgressBar: Improved performance using the DynamicTransform UsageHint.
- Notifications: Improved performance using the DynamicTransform UsageHint.
Fixes:
- Samples (Game): Added escape input action to dialogue player UIs.
- Samples (Game): Improved inventory layout.
- Samples (Components): Fixed NPEs caused by the new "Disable Other Views On Fade-In" option.

[1.0.2]
New:
- Added 'Add Default Escape Action' option to UIViewComponent which adds UIViewActionEscape that calls FadeOutAndDestroy. So you don't have to write script for simple escape with input.
- Samples: Added input support and icons to all three dialogue players
Fixes:
- Sample game, save/load view: Fix issue where the save button is not disabled when you are in the main menu

[1.0.1]
New:
- Added 'Disable Other Views On Fade-In' option to UIView and UIViewComponent
- Improved UI Element Manager API
Fixes:
- Game Sample: Fixed credits view
- Game Sample: Add custom navigation to main menu to be able to target quit button
- Game Sample: Fixed inventory item filter buttons
</pre>
</div>