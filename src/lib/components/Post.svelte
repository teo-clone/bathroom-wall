<script lang="ts">
	import { howLongAgo } from '$lib/utils/timeUtils';
	import PostMedia from './PostMedia.svelte';
	import type { Post } from '$lib/database.types';
	import PostShare from './PostShare.svelte';
	import PostVotes from './PostVotes.svelte';
	import WallContainer from './WallContainer.svelte';

	export let barUniqueName: string;
	export let barTimezone: string;
	export let post: Post;
</script>

<div id={`post_${post.id}`} class="transition duration-1000">
	<WallContainer>
		<div class="flex flex-col gap-2">
			<div class="flex justify-between px-5">
				<div class="flex gap-[3px]">
					<p class="font-bold">{post.nickname}</p>
				</div>
				<p class="text-sm text-gray-400">{howLongAgo(post.date, barTimezone)}</p>
			</div>

			<p class="px-5">{post.message}</p>

			{#if post.media}
				<PostMedia media={post.media} />
			{/if}

			<div class="flex justify-between px-5">
				<PostVotes {post} />
				<PostShare {post} {barUniqueName} />
			</div>
		</div>
	</WallContainer>
</div>
