<script lang="ts">
	import TileSeparator from './TileSeparator.svelte';

	export let barName: string | undefined = undefined;
</script>

<TileSeparator />

<div class="grid h-10 grid-cols-[140px_auto]">
	<div class="logo group flex text-xl font-bold">
		<a class="bg-black text-white group-hover:bg-white group-hover:text-black" href="/">
			<span class="rotate-[4deg] group-hover:-rotate-[4deg]">bath</span>
		</a>
		<a class="bg-white text-black group-hover:bg-black group-hover:text-white" href="/">
			<span class="-rotate-[4deg] group-hover:rotate-[4deg]">wall</span>
		</a>
		<a class="bg-black text-white group-hover:bg-white group-hover:text-black" href="/">
			<span class="rotate-[4deg] group-hover:-rotate-[4deg]">.co</span>
		</a>
	</div>

	<div class="flex items-center justify-end px-2">
		{#if !barName}
			a guest book for cafes and bars
		{:else}
			<h3 class="font-medium">{barName}</h3>
		{/if}
	</div>
</div>

<TileSeparator />

<style lang="postcss">
	.logo > a {
		display: flex;
		align-items: center;
		text-decoration: none;
		padding-left: 5px;
		padding-right: 5px;
	}
</style>
