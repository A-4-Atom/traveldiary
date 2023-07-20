<script>
	import { store } from '../../lib/store';
	import CardDetails from '../../components/CardDetails.svelte';
	// import { onMount, beforeUpdate, afterUpdate } from 'svelte';
	let searchText = '';
	let allCards = $store;

</script>

<header class="flex w-[99vw] shadow h-14 items-center">
	<a href="/" class="absolute left-0 text-cyan-600 font-extrabold text-l">Previous Page</a>
	<h1 class="mx-auto font-extrabold text-cyan-600 text-2xl">Travel Diary</h1>
</header>

<div class="my-5 w-[99vw] flex flex-col items-center justify-center">
	<input
		class="bg-cyan-400 appearance-none border-2 border-cyan-200 rounded w-1/2 py-2 px-4 text-gray-700 placeholder-gray-700 focus:outline-none focus:bg-white focus:border-cyan-300"
		type="text"
		placeholder="Search"
		bind:value={searchText}
	/>
	{#each allCards as card (card.id)}
		<div class="w-1/2 my-4">
			<CardDetails {...card} />
		</div>
	{/each}
</div>
