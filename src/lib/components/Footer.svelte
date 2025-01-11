<script>
	import { A } from 'flowbite-svelte';
	import { Button } from 'flowbite-svelte';
</script>

<footer class="px-4 py-2 shadow md:px-6 md:py-2 bg-stone-600 text-stone-50">
	<div class="md:flex md:items-center md:justify-between">
		<span class="text-sm sm:text-center"
			>© {new Date().getFullYear()}
			<A href="/">Cupkek Games</A>. All Rights Reserved.
		</span>
		<ul class="flex flex-wrap items-center mt-3 text-sm sm:mt-0">
			<li class="mr-4 md:mr-6">
				<A href="#">About</A>
			</li>
			<li class="mr-4 md:mr-6">
				<A href="#">Privacy Policy</A>
			</li>
			<li class="mr-4 md:mr-6">
				<A href="#">Terms of Service</A>
			</li>
			<!-- <li class="mr-4 md:mr-6">
				<SwitchTheme />
			</li> -->
		</ul>
	</div>
</footer>
