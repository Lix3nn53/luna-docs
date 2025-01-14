<script>
	import { Heading, P, A, Mark, Secondary, GradientButton, Hr, Li, List } from 'flowbite-svelte';
	import settings_system from '$lib/img/docs/views/settings_system.png';
	import settings_data from '$lib/img/docs/views/settings_data.jpg';
	import settings from '$lib/img/docs/views/settings.jpg';

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
	>Views/ Settings</Heading
>
<div class="p-4">
	<img alt="settings" src={settings} class="mb-6 max-w-2xl rounded-xl border-4" />
	<P
		>The Settings system provides complete functionality. The demo samples include a working example
		with Graphics, Audio, and Localization settings, which can be used as a starting point for your
		implementation.</P
	>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>SettingsSystem</Heading
	>
	<img alt="settings_system" src={settings_system} class="mb-6 max-w-xl rounded-xl border-4" />
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>SettingsDataSO</Heading
	>
	<P>ScriptableObject that contains dictionary of SettingsDataSection.</P>
	<img alt="settings_data" src={settings_data} class="mb-6 max-w-xl rounded-xl border-4" />
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>SettingsDataSection</Heading
	>
	<P
		>ScriptableObject, abstract class you have to implement to add custom sections to
		SettingsDataSO.</P
	>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl"
		>Example</Heading
	>
	<CodeBlock
		language="csharp"
		code={`
[CreateAssetMenu(fileName = "SectionGameplay", menuName = "CupkekGames/Settings/SectionGameplay")]
public class SettingsDataSectionGameplay : SettingsDataSection
{
    [SerializeField] private float _cursorSensitivity;

    public float CursorSensitivity
    {
        get => _cursorSensitivity;
        set
        {
            _cursorSensitivity = value;
            
            // Apply cursor sensitivity here
        }
    }

    public override bool Equals(object obj)
    {
        if (obj == null || GetType() != obj.GetType())
            return false;

        SettingsDataSectionGameplay b = (SettingsDataSectionGameplay)obj;
        return _cursorSensitivity == b._cursorSensitivity;
    }

    public override int GetHashCode()
    {
        return _cursorSensitivity.GetHashCode();
    }

    public override void SaveToPlayerPrefs(string key)
    {
        PlayerPrefs.SetFloat($"{key}_CursorSensitivity", _cursorSensitivity);
        PlayerPrefs.Save();
    }

    public override void LoadFromPlayerPrefs(string key)
    {
        if (PlayerPrefs.HasKey($"{key}_CursorSensitivity"))
        {
            _cursorSensitivity = PlayerPrefs.GetFloat($"{key}_CursorSensitivity");
        }
    }

    public override void CopyValuesFrom(SettingsDataSection section)
    {
        if (section is SettingsDataSectionGameplay copy)
        {
            _cursorSensitivity = copy._cursorSensitivity;
        }
    }

	/// <summary>
	/// Applies settings from another <see cref="SettingsDataSectionGameplay"/> instance.
	/// </summary>
	/// <param name="settingsData">
	/// The source <see cref="SettingsDataSectionGameplay"/> 
	/// instance containing the settings to apply.
	/// </param>
    public override void ApplySettings(SettingsDataSection settingsData)
    {
        if (settingsData is SettingsDataSectionGameplay copy)
        {
            CursorSensitivity = copy._cursorSensitivity;
        }
    }
}`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>SettingsMenuView</Heading
	>
	<P>Main view for Settings UI. Add view sections as a child to this object.</P>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>SettingsMenuViewSection</Heading
	>
	<P
		>MonoBehaviour, abstract class you have to implement to add custom sections to SettingsMenuView.</P
	>

	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl"
		>Example</Heading
	>
	<CodeBlock
		language="csharp"
		code={`
using UnityEngine.UIElements;
using CupkekGames.Core;

public class SettingsMenuViewAudio : SettingsMenuViewSection
{
private Slider _sliderCursorSensitivity;

protected override void Awake()
{
  base.Awake();

  _sliderCursorSensitivity = UIDocument.rootVisualElement.Q<Slider>("CursorSensitivitySlider");
}

public void OnEnable()
{
  _sliderCursorSensitivity.RegisterValueChangedCallback(OnSliderChanged);
}

public void OnDisable()
{
  _sliderCursorSensitivity.UnregisterValueChangedCallback(OnSliderChanged);
}

public override void ApplySettingsToUI()
{
  SettingsDataSectionGameplay gameplay = (SettingsDataSectionGameplay)_changedSettings.Dictionary["gameplay"];

  _sliderCursorSensitivity.value = gameplay.CursorSensitivity;
}

private void OnSliderChanged(ChangeEvent<int> evt)
{
  SettingsDataSectionGameplay gameplay = (SettingsDataSectionGameplay)_changedSettings.Dictionary["gameplay"];

  gameplay.CursorSensitivity = evt.newValue;
}
}`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
</div>
