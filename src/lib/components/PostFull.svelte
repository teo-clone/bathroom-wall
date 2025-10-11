<script lang="ts">
	import type { Post } from '$lib/database.types';
	import PostMedia from './PostMedia.svelte';

	export let post: Post;

	let rotation = -(Math.random() * 4) + -(Math.random() * 4);

	function formatDate(date: Date): string {
		const options: Intl.DateTimeFormatOptions = {
			month: 'short', // Use 'short' for abbreviated month
			day: 'numeric'
		};

		// Get the time in 24-hour format (e.g., 17:34)
		const time = date.toLocaleTimeString('en-US', {
			hour: '2-digit',
			minute: '2-digit',
			hour12: false
		});

		// Get the month and day part
		const monthDay = date.toLocaleDateString('en-US', options);

		// Get the short year manually
		const shortYear = `'${date.getFullYear().toString().slice(-2)}`;

		return `${time} - ${monthDay} ${shortYear}`;
	}
</script>

<div class="flex max-h-full max-w-[600px] flex-col gap-2 bg-white bg-opacity-90 p-4">
	{#if post.media}
		<PostMedia media={post.media} class="max-h-[70vh] w-full  object-contain" />
	{/if}

	{#if post.message}
		<div class="px-1 text-left text-sm">
			{post.message}
		</div>
	{/if}

	<div class="w-full px-1">
		<div class="flex w-full items-center justify-between text-xs">
			<div class="flex gap-1">
				# <p class="px-1">{post.nickname}</p>
			</div>
			<p class="italic">{formatDate(post.date)}</p>
		</div>
	</div>
</div>
