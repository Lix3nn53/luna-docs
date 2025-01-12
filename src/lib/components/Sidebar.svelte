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
	let itemClass = "flex items-center rounded px-2 py-2 my-0 text-sm hover:bg-violet-400/50";
	let activeClass = "bg-violet-500";
	let nonActiveClass = "hover:bg-violet-400/50"
	let dropdownWrapperClass = "flex items-center w-full rounded px-2 py-2 my-0 text-sm hover:bg-violet-400/50"
  let borderClass = 'pt-4 mt-4 border-t border-gray-200 dark:border-gray-400';

	let dropdownItemClass = itemClass + " ml-4 ps-4";
	let dropdownActiveClass = itemClass + " ml-4 ps-4 " + activeClass;

	$: activeUrl = $page.url.pathname;
</script>
  
  <Sidebar class="min-h-full" {activeUrl}>
	<SidebarWrapper class="min-h-full" divClass={"overflow-y-auto py-4 px-3 bg-stone-50 dark:bg-stone-800"}>
	  	<SidebarGroup>
			<SidebarBrand {site} />
			<SidebarItem class={itemClass} activeClass={activeClass} nonActiveClass={nonActiveClass} label="Introduction" href="/">
			<svelte:fragment slot="icon">
				<i class="fa-solid fa-door-open"></i>
			</svelte:fragment>
			</SidebarItem>
			<SidebarItem class={itemClass} activeClass={activeClass} nonActiveClass={nonActiveClass} label="Community" href="/community">
			<svelte:fragment slot="icon">
				<i class="fa-brands fa-discord"></i>
			</svelte:fragment>
			</SidebarItem>
			<SidebarItem class={itemClass} activeClass={activeClass} nonActiveClass={nonActiveClass} label="Games" href="/games">
			<svelte:fragment slot="icon">
				<i class="fa-solid fa-gamepad"></i>
			</svelte:fragment>
			</SidebarItem>
		</SidebarGroup>
		<SidebarGroup border {borderClass}>
			<div class="flex flex-row px-2 items-center">
				<i class="fa-solid fa-moon pr-2"></i>
				<Heading tag="h5" customSize="text-base font-bold">Luna UI</Heading>
			</div>
			<SidebarItem class={itemClass} activeClass={activeClass} nonActiveClass={nonActiveClass} label="Gallery" href="/luna/gallery" />
			<SidebarItem class={itemClass} activeClass={activeClass} nonActiveClass={nonActiveClass} label="Why UI Toolkit?" href="/luna/whyuitk" />
			<SidebarItem class={itemClass} activeClass={activeClass} nonActiveClass={nonActiveClass} label="Quick Start" href="/luna/quick" />
			<SidebarDropdownWrapper btnClass={dropdownWrapperClass} label="Samples" isOpen={activeUrl.includes("/luna/samples")}>
				<svelte:fragment slot="icon">
					<i class="fa-solid fa-box"></i>
				</svelte:fragment>
				<SidebarDropdownItem aClass={dropdownItemClass} activeClass={dropdownActiveClass} label="Components" href="/luna/samples/components" active={activeUrl.includes("/luna/samples/components")}/>
				<SidebarDropdownItem aClass={dropdownItemClass} activeClass={dropdownActiveClass} label="Game" href="/luna/samples/game" active={activeUrl.includes("/luna/samples/game")}/>
				<SidebarDropdownItem aClass={dropdownItemClass} activeClass={dropdownActiveClass} label="Game Addressables" href="/luna/samples/addressables" active={activeUrl.includes("/luna/samples/addressables")}/>
				<SidebarDropdownItem aClass={dropdownItemClass} activeClass={dropdownActiveClass} label="Localization" href="/luna/samples/localization" active={activeUrl.includes("/luna/samples/localization")}/>
			</SidebarDropdownWrapper>
			<SidebarDropdownWrapper btnClass={dropdownWrapperClass} label="Framework" isOpen={activeUrl.includes("/luna/framework")}>
				<svelte:fragment slot="icon">
					<i class="fa-solid fa-code"></i>
				</svelte:fragment>
				<SidebarDropdownItem aClass={dropdownItemClass} activeClass={dropdownActiveClass} label="UIView" href="/luna/framework/uiview" active={activeUrl.includes("/luna/framework/uiview")}/>
				<SidebarDropdownItem aClass={dropdownItemClass} activeClass={dropdownActiveClass} label="UIViewComponent" href="/luna/framework/uiviewcomponent" active={activeUrl.includes("/luna/framework/uiviewcomponent")}/>
				<SidebarDropdownItem aClass={dropdownItemClass} activeClass={dropdownActiveClass} label="FadeUIElement" href="/luna/framework/FadeUIElement" active={activeUrl.includes("/luna/framework/FadeUIElement")}/>
				<SidebarDropdownItem aClass={dropdownItemClass} activeClass={dropdownActiveClass} label="UIActions" href="/luna/framework/UIActions" active={activeUrl.includes("/luna/framework/UIActions")}/>
				<SidebarDropdownItem aClass={dropdownItemClass} activeClass={dropdownActiveClass} label="Example: Multi Page UI" href="/luna/framework/example" active={activeUrl.includes("/luna/framework/example")}/>
				<SidebarDropdownItem aClass={dropdownItemClass} activeClass={dropdownActiveClass} label="UIElementManager" href="/luna/framework/UIElementManager" active={activeUrl.includes("/luna/framework/UIElementManager")}/>
				<SidebarDropdownItem aClass={dropdownItemClass} activeClass={dropdownActiveClass} label="UI Navigation" href="/luna/framework/UINavigation" active={activeUrl.includes("/luna/framework/UINavigation")}/>
				<SidebarDropdownItem aClass={dropdownItemClass} activeClass={dropdownActiveClass} label="Localization" href="/luna/framework/localization" active={activeUrl.includes("/luna/framework/localization")}/>
				<SidebarDropdownItem aClass={dropdownItemClass} activeClass={dropdownActiveClass} label="Drag & Drop" href="/luna/framework/dragdrop" active={activeUrl.includes("/luna/framework/dragdrop")}/>
			</SidebarDropdownWrapper>
			<SidebarDropdownWrapper btnClass={dropdownWrapperClass} label="Components" isOpen={activeUrl.includes("/luna/components")}>
				<svelte:fragment slot="icon">
					<i class="fa-solid fa-layer-group"></i>
				</svelte:fragment>
				<SidebarDropdownItem aClass={dropdownItemClass} activeClass={dropdownActiveClass} label="UIView" href="/luna/framework/uiview" active={activeUrl.includes("/luna/framework/uiview")}/>
			</SidebarDropdownWrapper>
			<SidebarDropdownWrapper btnClass={dropdownWrapperClass} label="Views" isOpen={activeUrl.includes("/luna/views")}>
				<svelte:fragment slot="icon">
					<i class="fa-solid fa-window-restore"></i>
				</svelte:fragment>
				<SidebarDropdownItem aClass={dropdownItemClass} activeClass={dropdownActiveClass} label="UIView" href="/luna/framework/uiview" active={activeUrl.includes("/luna/framework/uiview")}/>
			</SidebarDropdownWrapper>
			<SidebarDropdownWrapper btnClass={dropdownWrapperClass} label="Styling" isOpen={activeUrl.includes("/luna/styling")}>
				<svelte:fragment slot="icon">
					<i class="fa-solid fa-palette"></i>
				</svelte:fragment>
				<SidebarDropdownItem aClass={dropdownItemClass} activeClass={dropdownActiveClass} label="UIView" href="/luna/framework/uiview" active={activeUrl.includes("/luna/framework/uiview")}/>
			</SidebarDropdownWrapper>
		</SidebarGroup>
		<SidebarGroup border {borderClass}>
			<SidebarDropdownWrapper btnClass={dropdownWrapperClass} label="Core Library" isOpen={activeUrl.includes("/core")}>
				<svelte:fragment slot="icon">
					<i class="fa-solid fa-gears"></i>
				</svelte:fragment>
				<SidebarDropdownItem aClass={dropdownItemClass} activeClass={dropdownActiveClass} label="Service Locator" href="/core/servicelocator" active={activeUrl.includes("/core/servicelocator")}/>
				<SidebarDropdownItem aClass={dropdownItemClass} activeClass={dropdownActiveClass} label="Scene Management Addressable" href="/core/scenemanagementaddressable" active={activeUrl.includes("/core/scenemanagementaddressable")}/>
				<SidebarDropdownItem aClass={dropdownItemClass} activeClass={dropdownActiveClass} label="KeyValue Database" href="/core/KeyValueDatabase" active={activeUrl.includes("/core/KeyValueDatabase")}/>
				<SidebarDropdownItem aClass={dropdownItemClass} activeClass={dropdownActiveClass} label="Prefab Loader" href="/core/prefabloader" active={activeUrl.includes("/core/prefabloader")}/>
				<SidebarDropdownItem aClass={dropdownItemClass} activeClass={dropdownActiveClass} label="Addressable Asset Manager" href="/core/addressableassetmanager" active={activeUrl.includes("/core/addressableassetmanager")}/>
				<SidebarDropdownItem aClass={dropdownItemClass} activeClass={dropdownActiveClass} label="Pool" href="/core/pool" active={activeUrl.includes("/core/pool")}/>
				<SidebarDropdownItem aClass={dropdownItemClass} activeClass={dropdownActiveClass} label="Fadeable" href="/core/fadeable" active={activeUrl.includes("/core/fadeable")}/>
				<SidebarDropdownItem aClass={dropdownItemClass} activeClass={dropdownActiveClass} label="Input Escape Manager" href="/core/inputescapemanager" active={activeUrl.includes("/core/inputescapemanager")}/>
				<SidebarDropdownItem aClass={dropdownItemClass} activeClass={dropdownActiveClass} label="Game Save Manager" href="/core/gamesavemanager" active={activeUrl.includes("/core/gamesavemanager")}/>
				<SidebarDropdownItem aClass={dropdownItemClass} activeClass={dropdownActiveClass} label="Behaviour Tree" href="/core/behaviourtree" active={activeUrl.includes("/core/behaviourtree")}/>
			</SidebarDropdownWrapper>
		</SidebarGroup>
	</SidebarWrapper>
  </Sidebar>