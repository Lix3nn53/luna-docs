<script lang="ts">
	import { page } from '$app/state';
	import {
		Sidebar,
		SidebarGroup,
		SidebarItem,
		SidebarWrapper,
		SidebarDropdownItem,
		SidebarDropdownWrapper
	} from 'flowbite-svelte';
	import { SidebarBrand, Heading, P, A } from 'flowbite-svelte';
	import logo from '$lib/img/logo128.png';

	let site = {
		name: 'CupkekGames',
		href: '/',
		img: logo
	};

	let spanClass = 'flex-1 ms-3 whitespace-nowrap';
	let itemClass = 'flex items-center rounded px-2 py-2 my-0 text-sm hover:bg-violet-400/50';
	let activeClass = 'bg-violet-500';
	let nonActiveClass = 'hover:bg-violet-400/50';
	let dropdownWrapperClass =
		'flex items-center w-full rounded px-2 py-2 my-0 text-sm hover:bg-violet-400/50';
	let borderClass = 'pt-4 mt-4 border-t border-gray-200 dark:border-gray-400';

	let dropdownItemClass = itemClass + ' ml-4 ps-4';
	let dropdownActiveClass = itemClass + ' ml-4 ps-4 ' + activeClass;
</script>

<Sidebar class="min-h-full" activeUrl={page.url.pathname}>
	<SidebarWrapper
		class="min-h-full"
		divClass={'overflow-y-auto py-4 px-3 bg-stone-50 dark:bg-stone-800'}
	>
		<SidebarGroup>
			<SidebarBrand {site} />
			<SidebarItem class={itemClass} {activeClass} {nonActiveClass} label="Introduction" href="/">
				<svelte:fragment slot="icon">
					<i class="fa-solid fa-door-open"></i>
				</svelte:fragment>
			</SidebarItem>
			<SidebarItem
				class={itemClass}
				{activeClass}
				{nonActiveClass}
				label="Community"
				href="/community"
			>
				<svelte:fragment slot="icon">
					<i class="fa-brands fa-discord"></i>
				</svelte:fragment>
			</SidebarItem>
			<SidebarItem class={itemClass} {activeClass} {nonActiveClass} label="Games" href="/games">
				<svelte:fragment slot="icon">
					<i class="fa-solid fa-gamepad"></i>
				</svelte:fragment>
			</SidebarItem>
		</SidebarGroup>
		<SidebarGroup border {borderClass}>
			<div class="flex flex-row items-center px-2">
				<i class="fa-solid fa-moon pr-2"></i>
				<Heading tag="h5" customSize="text-base font-bold">Luna UI</Heading>
			</div>
			<SidebarItem
				class={itemClass}
				{activeClass}
				{nonActiveClass}
				label="Gallery"
				href="/luna/gallery"
			/>
			<SidebarItem
				class={itemClass}
				{activeClass}
				{nonActiveClass}
				label="Why UI Toolkit?"
				href="/luna/whyuitk"
			/>
			<SidebarItem
				class={itemClass}
				{activeClass}
				{nonActiveClass}
				label="Quick Start"
				href="/luna/quickstart"
			/>
			<SidebarItem
				class={itemClass}
				{activeClass}
				{nonActiveClass}
				label="Troubleshoot"
				href="/luna/troubleshoot"
			/>
			<SidebarDropdownWrapper
				btnClass={dropdownWrapperClass}
				label="Samples"
				isOpen={page.url.pathname.includes('/luna/samples')}
			>
				<svelte:fragment slot="icon">
					<i class="fa-solid fa-box"></i>
				</svelte:fragment>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="Components"
					href="/luna/samples/components"
					active={page.url.pathname === '/luna/samples/components'}
				/>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="Game"
					href="/luna/samples/game"
					active={page.url.pathname === '/luna/samples/game'}
				/>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="Game Addressables"
					href="/luna/samples/addressables"
					active={page.url.pathname === '/luna/samples/addressables'}
				/>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="Localization"
					href="/luna/samples/localization"
					active={page.url.pathname === '/luna/samples/localization'}
				/>
			</SidebarDropdownWrapper>
			<SidebarDropdownWrapper
				btnClass={dropdownWrapperClass}
				label="Framework"
				isOpen={page.url.pathname.includes('/luna/framework')}
			>
				<svelte:fragment slot="icon">
					<i class="fa-solid fa-code"></i>
				</svelte:fragment>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="UIView"
					href="/luna/framework/uiview"
					active={page.url.pathname === '/luna/framework/uiview'}
				/>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="UIViewComponent"
					href="/luna/framework/uiviewcomponent"
					active={page.url.pathname === '/luna/framework/uiviewcomponent'}
				/>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="FadeUIElement"
					href="/luna/framework/fadeuielement"
					active={page.url.pathname === '/luna/framework/fadeuielement'}
				/>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="UI Actions"
					href="/luna/framework/uiactions"
					active={page.url.pathname === '/luna/framework/uiactions'}
				/>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="Example: Multi Page UI"
					href="/luna/framework/example01"
					active={page.url.pathname === '/luna/framework/example01'}
				/>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="UI Element Manager"
					href="/luna/framework/uielementmanager"
					active={page.url.pathname === '/luna/framework/uielementmanager'}
				/>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="UI Navigation"
					href="/luna/framework/uinavigation"
					active={page.url.pathname === '/luna/framework/uinavigation'}
				/>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="Localization"
					href="/luna/framework/localization"
					active={page.url.pathname === '/luna/framework/localization'}
				/>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="Drag & Drop"
					href="/luna/framework/dragdrop"
					active={page.url.pathname === '/luna/framework/dragdrop'}
				/>
			</SidebarDropdownWrapper>
			<SidebarDropdownWrapper
				btnClass={dropdownWrapperClass}
				label="Components"
				isOpen={page.url.pathname.includes('/luna/components')}
			>
				<svelte:fragment slot="icon">
					<i class="fa-solid fa-layer-group"></i>
				</svelte:fragment>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="Guide"
					href="/luna/components/guide"
					active={page.url.pathname === '/luna/components/guide'}
				/>
				<div class="ml-4 flex flex-row items-center ps-2">
					<Heading tag="h5" customSize="text-sm underline underline-offset-4"
						>Built-in Components</Heading
					>
				</div>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="Button"
					href="/luna/components/button"
					active={page.url.pathname === '/luna/components/button'}
				/>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="Slider"
					href="/luna/components/slider"
					active={page.url.pathname === '/luna/components/slider'}
				/>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="Dropdown"
					href="/luna/components/dropdown"
					active={page.url.pathname === '/luna/components/dropdown'}
				/>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="Toggle"
					href="/luna/components/toggle"
					active={page.url.pathname === '/luna/components/toggle'}
				/>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="Radio Button Group"
					href="/luna/components/radiobuttongroup"
					active={page.url.pathname === '/luna/components/radiobuttongroup'}
				/>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="List & ScrollView"
					href="/luna/components/list"
					active={page.url.pathname === '/luna/components/list'}
				/>
				<div class="ml-4 flex flex-row items-center ps-2">
					<Heading tag="h5" customSize="text-sm underline underline-offset-4"
						>Custom Components</Heading
					>
				</div>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="Input Prompt"
					href="/luna/components/inputprompt"
					active={page.url.pathname === '/luna/components/inputprompt'}
				/>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="Progress Bar"
					href="/luna/components/progressbar"
					active={page.url.pathname === '/luna/components/progressbar'}
				/>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="Radial Progress Bar"
					href="/luna/components/radialprogressbar"
					active={page.url.pathname === '/luna/components/radialprogressbar'}
				/>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="Radial Loading"
					href="/luna/components/radialloading"
					active={page.url.pathname === '/luna/components/radialloading'}
				/>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="Tooltip"
					href="/luna/components/tooltip"
					active={page.url.pathname === '/luna/components/tooltip'}
				/>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="Pie Chart"
					href="/luna/components/piechart"
					active={page.url.pathname === '/luna/components/piechart'}
				/>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="Tabview"
					href="/luna/components/tabview"
					active={page.url.pathname === '/luna/components/tabview'}
				/>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="Confirmation Popup"
					href="/luna/components/confirmationpopup"
					active={page.url.pathname === '/luna/components/confirmationpopup'}
				/>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="Notifications"
					href="/luna/components/notifications"
					active={page.url.pathname === '/luna/components/notifications'}
				/>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="Pagination"
					href="/luna/components/pagination"
					active={page.url.pathname === '/luna/components/pagination'}
				/>
			</SidebarDropdownWrapper>
			<SidebarDropdownWrapper
				btnClass={dropdownWrapperClass}
				label="Views"
				isOpen={page.url.pathname.includes('/luna/views')}
			>
				<svelte:fragment slot="icon">
					<i class="fa-solid fa-window-restore"></i>
				</svelte:fragment>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="Loading"
					href="/luna/views/loading"
					active={page.url.pathname === '/luna/views/loading'}
				/>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="Main Menu"
					href="/luna/views/mainmenu"
					active={page.url.pathname === '/luna/views/mainmenu'}
				/>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="Settings"
					href="/luna/views/settings"
					active={page.url.pathname === '/luna/views/settings'}
				/>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="Save & Load"
					href="/luna/views/saveload"
					active={page.url.pathname === '/luna/views/saveload'}
				/>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="Credits"
					href="/luna/views/credits"
					active={page.url.pathname === '/luna/views/credits'}
				/>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="Pause Menu"
					href="/luna/views/pausemenu"
					active={page.url.pathname === '/luna/views/pausemenu'}
				/>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="Inventory"
					href="/luna/views/inventory"
					active={page.url.pathname === '/luna/views/inventory'}
				/>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="Visual Novel"
					href="/luna/views/visualnovel"
					active={page.url.pathname === '/luna/views/visualnovel'}
				/>
			</SidebarDropdownWrapper>
			<SidebarDropdownWrapper
				btnClass={dropdownWrapperClass}
				label="Styling"
				isOpen={page.url.pathname.includes('/luna/styling')}
			>
				<svelte:fragment slot="icon">
					<i class="fa-solid fa-palette"></i>
				</svelte:fragment>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="USS Guide"
					href="/luna/styling/ussguide"
					active={page.url.pathname === '/luna/styling/ussguide'}
				/>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="Colors"
					href="/luna/styling/colors"
					active={page.url.pathname === '/luna/styling/colors'}
				/>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="Size"
					href="/luna/styling/size"
					active={page.url.pathname === '/luna/styling/size'}
				/>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="Layout"
					href="/luna/styling/layout"
					active={page.url.pathname === '/luna/styling/layout'}
				/>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="Text"
					href="/luna/styling/text"
					active={page.url.pathname === '/luna/styling/text'}
				/>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="Cursor"
					href="/luna/styling/cursor"
					active={page.url.pathname === '/luna/styling/cursor'}
				/>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="Border"
					href="/luna/styling/border"
					active={page.url.pathname === '/luna/styling/border'}
				/>
			</SidebarDropdownWrapper>
		</SidebarGroup>
		<SidebarGroup border {borderClass}>
			<SidebarDropdownWrapper
				btnClass={dropdownWrapperClass}
				label="UI Toolkit Guides"
				isOpen={page.url.pathname.includes('/uitkguide')}
			>
				<svelte:fragment slot="icon">
					<i class="fa-solid fa-book"></i>
				</svelte:fragment>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="ListView"
					href="/uitkguide/listview"
					active={page.url.pathname === '/uitkguide/listview'}
				/>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="USS Variables"
					href="/uitkguide/ussvariables"
					active={page.url.pathname === '/uitkguide/ussvariables'}
				/>
			</SidebarDropdownWrapper>
		</SidebarGroup>
		<SidebarGroup border {borderClass}>
			<SidebarDropdownWrapper
				btnClass={dropdownWrapperClass}
				label="Core Library"
				isOpen={page.url.pathname.includes('/core')}
			>
				<svelte:fragment slot="icon">
					<i class="fa-solid fa-gears"></i>
				</svelte:fragment>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="Fadeable"
					href="/core/fadeable"
					active={page.url.pathname === '/core/fadeable'}
				/>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="Input Escape Manager"
					href="/core/inputescapemanager"
					active={page.url.pathname === '/core/inputescapemanager'}
				/>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="Game Save Manager"
					href="/core/gamesavemanager"
					active={page.url.pathname === '/core/gamesavemanager'}
				/>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="KeyValue Database"
					href="/core/KeyValueDatabase"
					active={page.url.pathname === '/core/KeyValueDatabase'}
				/>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="Prefab Loader"
					href="/core/prefabloader"
					active={page.url.pathname === '/core/prefabloader'}
				/>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="Addressable Asset Manager"
					href="/core/addressableassetmanager"
					active={page.url.pathname === '/core/addressableassetmanager'}
				/>
				<SidebarDropdownItem
					aClass={dropdownItemClass}
					activeClass={dropdownActiveClass}
					label="Scene Management Addressable"
					href="/core/scenemanagementaddressable"
					active={page.url.pathname === '/core/scenemanagementaddressable'}
				/>
			</SidebarDropdownWrapper>
		</SidebarGroup>
	</SidebarWrapper>
</Sidebar>
