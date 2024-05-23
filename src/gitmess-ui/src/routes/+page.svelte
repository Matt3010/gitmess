<script lang="ts">
	import { getRepositories } from '$lib/api';
	import type { GitRepository } from '$lib/models/api.model';
	import { onMount } from 'svelte';
	import DeleteRepo from '$lib/components/DeleteRepo.svelte';

	let repositories: GitRepository[] = [];

	onMount(async () => {
		repositories = await getRepositories();
	});
</script>

<div class="card p-4">
	<header>
		<h3 class="h3">Repos</h3>
	</header>
	<article class="mt-4">
		<nav class="list-nav">
			<ul>
				{#each repositories as repository}
					<li class="flex">
						<a href="/repositories/{repository.name}/tree/main" class="w-full">
							<div>
								<span class="badge">📁</span>
								<span class="flex-auto">{repository.name}</span>
							</div>
						</a>
						<DeleteRepo repoName={repository.name} />
					</li>
				{/each}
			</ul>
		</nav>
	</article>
</div>
