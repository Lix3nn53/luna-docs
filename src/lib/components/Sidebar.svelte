<script lang="ts">
	import { page } from '$app/stores';
	import { Sidebar, SidebarGroup, SidebarItem, SidebarWrapper, SidebarDropdownItem, SidebarDropdownWrapper } from 'flowbite-svelte';
	import { SidebarBrand, Heading, P, A } from 'flowbite-svelte';
	import logo from '$lib/img/logo128.png';

	let site = {
		name: 'CupkekGames',
		href: '/',
		img: logo
	};

	let spanClass = 'flex-1 ms-3 whitespace-nowrap';
	let itemClass = "flex items-center rounded px-2 py-2 my-0 text-sm";
	let activeClass = "bg-violet-400";

	let dropdownItemClass = itemClass + " ps-8";

	$: activeUrl = $page.url.pathname;
</script>
  
  <Sidebar class="min-h-full" {activeUrl}>
	<SidebarWrapper class="min-h-full" divClass={"overflow-y-auto py-4 px-3 bg-stone-50 dark:bg-stone-800"}>
	  	<SidebarGroup>
			<SidebarBrand {site} />
			<SidebarItem class={itemClass} activeClass={activeClass} label="Introduction" href="/">
			<svelte:fragment slot="icon">
				<i class="fa-regular fa-hand-point-right"></i>
			</svelte:fragment>
			</SidebarItem>
			<SidebarItem class={itemClass} activeClass={activeClass} label="Community" href="/community">
			<svelte:fragment slot="icon">
				<i class="fa-brands fa-discord"></i>
			</svelte:fragment>
			</SidebarItem>
		</SidebarGroup>
		<SidebarGroup border>
			<div class="flex flex-row px-2 items-center">
				<i class="fa-solid fa-paw pr-2"></i>
				<Heading tag="h5" customSize="text-base font-bold">Luna UI</Heading>
			</div>
			<SidebarItem class={itemClass} activeClass={activeClass} label="Gallery" href="/luna/gallery" />
			<SidebarItem class={itemClass} activeClass={activeClass} label="Why UI Toolkit?" href="/luna/whyuitk" />
			<SidebarItem class={itemClass} activeClass={activeClass} label="Quick Start" href="/luna/quick" />
			<SidebarDropdownWrapper class={itemClass} label="Samples" isOpen={activeUrl.includes("/luna/samples")}>
				<svelte:fragment slot="icon">
					<i class="fa-solid fa-box"></i>
				</svelte:fragment>
				<SidebarDropdownItem class={dropdownItemClass} activeClass={activeClass} label="Essentials" href="/luna/samples/essentials" active={activeUrl.includes("/luna/samples/essentials")}/>
				<SidebarDropdownItem class={dropdownItemClass} activeClass={activeClass} label="Components" href="/luna/samples/components" active={activeUrl.includes("/luna/samples/components")}/>
				<SidebarDropdownItem class={dropdownItemClass} activeClass={activeClass} label="Game" href="/luna/samples/game" active={activeUrl.includes("/luna/samples/game")}/>
				<SidebarDropdownItem class={dropdownItemClass} activeClass={activeClass} label="Game Addressables" href="/luna/samples/addressables" active={activeUrl.includes("/luna/samples/addressables")}/>
				<SidebarDropdownItem class={dropdownItemClass} activeClass={activeClass} label="Localization" href="/luna/samples/localization" active={activeUrl.includes("/luna/samples/localization")}/>
			</SidebarDropdownWrapper>
			<SidebarDropdownWrapper class={itemClass} label="Framework" isOpen={activeUrl.includes("/luna/framework")}>
				<svelte:fragment slot="icon">
					<i class="fa-solid fa-code"></i>
				</svelte:fragment>
				<SidebarDropdownItem class={dropdownItemClass} activeClass={activeClass} label="UIView" href="/luna/framework/uiview" active={activeUrl.includes("/luna/framework/uiview")}/>
				<SidebarDropdownItem class={dropdownItemClass} activeClass={activeClass} label="UIViewComponent" href="/luna/framework/uiviewcomponent" active={activeUrl.includes("/luna/framework/uiviewcomponent")}/>
				<SidebarDropdownItem class={dropdownItemClass} activeClass={activeClass} label="FadeUIElement" href="/luna/framework/FadeUIElement" active={activeUrl.includes("/luna/framework/FadeUIElement")}/>
				<SidebarDropdownItem class={dropdownItemClass} activeClass={activeClass} label="UIActions" href="/luna/framework/UIActions" active={activeUrl.includes("/luna/framework/UIActions")}/>
				<SidebarDropdownItem class={dropdownItemClass} activeClass={activeClass} label="Example: Multi Page UI" href="/luna/framework/example" active={activeUrl.includes("/luna/framework/example")}/>
				<SidebarDropdownItem class={dropdownItemClass} activeClass={activeClass} label="UIElementManager" href="/luna/framework/UIElementManager" active={activeUrl.includes("/luna/framework/UIElementManager")}/>
				<SidebarDropdownItem class={dropdownItemClass} activeClass={activeClass} label="UI Navigation" href="/luna/framework/UINavigation" active={activeUrl.includes("/luna/framework/UINavigation")}/>
				<SidebarDropdownItem class={dropdownItemClass} activeClass={activeClass} label="Localization" href="/luna/framework/localization" active={activeUrl.includes("/luna/framework/localization")}/>
				<SidebarDropdownItem class={dropdownItemClass} activeClass={activeClass} label="Drag & Drop" href="/luna/framework/dragdrop" active={activeUrl.includes("/luna/framework/dragdrop")}/>
			</SidebarDropdownWrapper>
			<SidebarDropdownWrapper class={itemClass} label="Components" isOpen={activeUrl.includes("/luna/components")}>
				<svelte:fragment slot="icon">
					<i class="fa-solid fa-layer-group"></i>
				</svelte:fragment>
				<SidebarDropdownItem class={dropdownItemClass} activeClass={activeClass} label="UIView" href="/luna/framework/uiview" active={activeUrl.includes("/luna/framework/uiview")}/>
			</SidebarDropdownWrapper>
			<SidebarDropdownWrapper class={itemClass} label="Views" isOpen={activeUrl.includes("/luna/views")}>
				<svelte:fragment slot="icon">
					<i class="fa-solid fa-window-restore"></i>
				</svelte:fragment>
				<SidebarDropdownItem class={dropdownItemClass} activeClass={activeClass} label="UIView" href="/luna/framework/uiview" active={activeUrl.includes("/luna/framework/uiview")}/>
			</SidebarDropdownWrapper>
			<SidebarDropdownWrapper class={itemClass} label="Styling" isOpen={activeUrl.includes("/luna/styling")}>
				<svelte:fragment slot="icon">
					<i class="fa-solid fa-palette"></i>
				</svelte:fragment>
				<SidebarDropdownItem class={dropdownItemClass} activeClass={activeClass} label="UIView" href="/luna/framework/uiview" active={activeUrl.includes("/luna/framework/uiview")}/>
			</SidebarDropdownWrapper>
		</SidebarGroup>
		<SidebarGroup border>
			<SidebarDropdownWrapper class={itemClass} label="Core Library" isOpen={activeUrl.includes("/core")}>
				<svelte:fragment slot="icon">
					<i class="fa-solid fa-gears"></i>
				</svelte:fragment>
				<SidebarDropdownItem class={dropdownItemClass} activeClass={activeClass} label="Service Locator" href="/core/servicelocator" active={activeUrl.includes("/core/servicelocator")}/>
				<SidebarDropdownItem class={dropdownItemClass} activeClass={activeClass} label="Scene Management Addressable" href="/core/scenemanagementaddressable" active={activeUrl.includes("/core/scenemanagementaddressable")}/>
				<SidebarDropdownItem class={dropdownItemClass} activeClass={activeClass} label="KeyValue Database" href="/core/KeyValueDatabase" active={activeUrl.includes("/core/KeyValueDatabase")}/>
				<SidebarDropdownItem class={dropdownItemClass} activeClass={activeClass} label="Prefab Loader" href="/core/prefabloader" active={activeUrl.includes("/core/prefabloader")}/>
				<SidebarDropdownItem class={dropdownItemClass} activeClass={activeClass} label="Addressable Asset Manager" href="/core/addressableassetmanager" active={activeUrl.includes("/core/addressableassetmanager")}/>
				<SidebarDropdownItem class={dropdownItemClass} activeClass={activeClass} label="Pool" href="/core/pool" active={activeUrl.includes("/core/pool")}/>
				<SidebarDropdownItem class={dropdownItemClass} activeClass={activeClass} label="Fadeable" href="/core/fadeable" active={activeUrl.includes("/core/fadeable")}/>
				<SidebarDropdownItem class={dropdownItemClass} activeClass={activeClass} label="Input Escape Manager" href="/core/inputescapemanager" active={activeUrl.includes("/core/inputescapemanager")}/>
				<SidebarDropdownItem class={dropdownItemClass} activeClass={activeClass} label="Game Save Manager" href="/core/gamesavemanager" active={activeUrl.includes("/core/gamesavemanager")}/>
				<SidebarDropdownItem class={dropdownItemClass} activeClass={activeClass} label="Behaviour Tree" href="/core/behaviourtree" active={activeUrl.includes("/core/behaviourtree")}/>
			</SidebarDropdownWrapper>
		</SidebarGroup>
	</SidebarWrapper>
  </Sidebar>