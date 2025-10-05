<script>
	import { Heading, P, Alert } from 'flowbite-svelte';

	import { CodeBlock } from 'svhighlight';
	import 'highlight.js/styles/base16/papercolor-dark.css';
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl"
	>Utility/ TransitionToggleRepeat</Heading
>
<div class="p-4">
	<P>
		<b>TransitionToggleRepeat</b> helps you loop UI Toolkit transitions effortlessly by toggling a USS class at the end of each transition. Use it to create repeating animations like pulsing buttons, bouncing icons, or rotating avatars without coroutines.
	</P>

	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Quick Start</Heading
	>
	<CodeBlock
		language="csharp"
		code={`using CupkekGames.Luna;
using UnityEngine.UIElements;

// Given a VisualElement 'button' and a USS class 'pulse'
TransitionToggleRepeat transition = new TransitionToggleRepeat(button, "pulse", 200);
transition.Start(0); // start immediately; call Pause() to stop`}
		showHeader={true}
		showLineNumbers={true}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>

	<Alert border class="my-4">
		<div class="flex flex-row">
			<i class="fa-solid fa-circle-info fa-2xl mr-4 mt-4"></i>
			<div>
				<P class="mb-2">
					The USS class you pass (e.g., <code>pulse</code>) must define a transition on at least one property; otherwise the <code>TransitionEndEvent</code> will not fire and the loop won't continue.
				</P>
			</div>
		</div>
	</Alert>

	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Required USS</Heading
	>
	<P>Example USS that scales an element up and down forever:</P>
	<CodeBlock
		language="css"
		code={`.pulse {
	  transition-timing-function: ease-in-out-sine;
	  transition-duration: 0.8s;
	  transition-property: scale;
	  /* toggling this class flips between default scale and 1.08 */
	  scale: 1.08;
	}

	/* Default state: no class applied */
	.button {
	  scale: 1;
	}`}
		showHeader={false}
		showLineNumbers={true}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>

	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>API</Heading
	>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>Constructor</Heading
	>
	<CodeBlock
		language="csharp"
		code={`public TransitionToggleRepeat(VisualElement ve, string ussClassName, int delayMsInterval);`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<P>
		<b>Parameters</b> — <code>ve</code>: target element, <code>ussClassName</code>: class to toggle, <code>delayMsInterval</code>: delay between repeats after each transition ends.
	</P>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>Methods</Heading
	>
	<CodeBlock
		language="csharp"
		code={`public void Start(long delayMs); // begins toggling after an initial delay
public void Pause();        // stops repeating and unregisters callbacks`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<P>
		Internally, it listens for <code>TransitionEndEvent</code> and then schedules the next toggle using <code>ve.schedule</code> with the configured delay.
	</P>

	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Example: Rotating avatars loop</Heading
	>
	<P>
		This sample randomizes avatar sprites and rotates each one forever by toggling the <code>avatar_anim_rotate</code> class with a small delay between cycles.
	</P>
	<CodeBlock
		language="csharp"
		code={`using System.Collections.Generic;
using System.Linq;
using CupkekGames.Luna;
using UnityEngine;
using UnityEngine.UIElements;

namespace CupkekGames.HeroManager
{
    public class AnimatedAvatars
    {
        private readonly List<Sprite> _avatars;
        private readonly List<VisualElement> _avatarElements;
        private readonly List<TransitionToggleRepeat> _transitions = new();

        public AnimatedAvatars(List<Sprite> avatars, List<VisualElement> avatarElements)
        {
            _avatars = avatars;
            _avatarElements = avatarElements;

            foreach (VisualElement avatar in _avatarElements)
            {
                _transitions.Add(new TransitionToggleRepeat(avatar, "avatar_anim_rotate", 200));
            }
        }

        public void StartAnimation()
        {
            RandomizeAvatars();
            foreach (TransitionToggleRepeat transition in _transitions)
            {
                transition.Start((long)0.2f);
            }
        }

        public void StopAnimation()
        {
            foreach (TransitionToggleRepeat transition in _transitions)
            {
                transition.Pause();
            }
        }

        private void RandomizeAvatars()
        {
            List<int> shuffledIndices = Enumerable.Range(0, _avatars.Count).OrderBy(_ => Random.value).ToList();

            for (int i = 0; i < _avatarElements.Count; i++)
            {
                if (i >= shuffledIndices.Count)
                {
                    VisualElement parentElement = _avatarElements[i].parent;
                    if (parentElement != null)
                    {
                        parentElement.style.display = DisplayStyle.None;
                    }
                    continue;
                }

                _avatarElements[i].style.backgroundImage = new StyleBackground(_avatars[shuffledIndices[i]]);
            }
        }
    }
}`}
		showHeader={true}
		showLineNumbers={true}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>

	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Reference implementation</Heading
	>
	<P>
		For clarity, here is the minimal implementation used by the utility:
	</P>
	<CodeBlock
		language="csharp"
		code={`using System;
using UnityEngine;
using UnityEngine.UIElements;

namespace CupkekGames.Luna
{
    public class TransitionToggleRepeat
    {
        private VisualElement _ve;
        private string _ussClassName;
        private int _delayMsInterval;
        private IVisualElementScheduledItem _schedule;

        public TransitionToggleRepeat(VisualElement ve, string ussClassName, int delayMsInterval)
        {
            _ve = ve;
            _ussClassName = ussClassName;
            _delayMsInterval = delayMsInterval;
        }

        public void Start(long delayMs)
        {
            if (_schedule != null)
            {
                return; // already playing
            }

            _ve.RegisterCallback<TransitionEndEvent>(OnTransitionEnd);
            _schedule = _ve.schedule.Execute(() => _ve.ToggleInClassList(_ussClassName)).StartingIn(delayMs);
        }

        private void OnTransitionEnd(TransitionEndEvent evt)
        {
            _ve.schedule.Execute(() => _ve.ToggleInClassList(_ussClassName)).StartingIn(_delayMsInterval);
        }

        public void Pause()
        {
            if (_schedule != null)
            {
                _schedule.Pause();
                _ve.UnregisterCallback<TransitionEndEvent>(OnTransitionEnd);
                _schedule = null;
            }
        }
    }
}`}
		showHeader={false}
		showLineNumbers={true}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>

	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Tips</Heading
	>
	<ul class="list-disc ml-6 space-y-1">
		<li>Ensure the toggled class changes a property with an active <code>transition</code>.</li>
		<li>Prefer short intervals (100–300ms) for snappy effects; longer for idle loops.</li>
		<li>Use <code>Pause()</code> when the element is hidden or off-screen to save CPU.</li>
		<li>Combine with different classes per element for subtle variety.</li>
	</ul>
</div>
