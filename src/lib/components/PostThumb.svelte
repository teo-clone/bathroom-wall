<script lang="ts">
	import type { Post } from '$lib/database.types';
	import PostMedia from './PostMedia.svelte';
	import PostFull from './PostFull.svelte';

	export let post: Post;

	let showLightbox = false;

	function handleClick() {
		showLightbox = true;
	}

	function closeLightbox() {
		showLightbox = false;
	}

	const rotation = 16 * Math.random() - 8;
</script>

<button class="!aspect-square border-b border-r p-1" on:click={handleClick}>
	{#if post.media}
		<PostMedia media={post.media} class="aspect-square object-cover" />
	{:else if post.message}
		<div class={'line-clamp-6 h-full p-4 text-left text-xl'}>
			{post.message}
		</div>
	{/if}
</button>

{#if showLightbox}
	<button
		class="fixed inset-0 z-50 flex items-center justify-center bg-black bg-opacity-90 p-4"
		on:click={closeLightbox}
	>
		<div class="max-h-full max-w-full overflow-auto">
			<PostFull {post} />
		</div>
	</button>
{/if}

<style lang="postcss">
</style>
