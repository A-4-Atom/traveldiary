<script>
	export let isOpen;
	export let closeModal;
	import { store } from '../lib/store';

	let title;
	let location;
	let googleMapsUrl;
	let startDate;
	let endDate;
	let description;
	let imageUrl;

	function addCard() {
		if (!title) return;
		let allCards = [...$store];
		let id = allCards.length + 1;
		let newCard = { title, location, googleMapsUrl, startDate, endDate, description, imageUrl, id };
		allCards.push(newCard);
		store.set(allCards)

		// Resetting all values upon adding then closing the modal
		title = "";
		location = "";
		googleMapsUrl = "";
		startDate = "";
		endDate = "";
		description = "";
		imageUrl = "";

		closeModal()
		
	}
</script>

<div
	class="fixed inset-0 flex items-center justify-center z-50"
	style="display: {isOpen ? 'flex' : 'none'}"
>
	<div class="bg-white p-4 rounded shadow-md sm:w-1/2 w-5/6">
		<h2 class="text-lg font-semibold mb-2 text-cyan-500">Title</h2>
		<input type="text" class="w-full border rounded px-2 py-1" bind:value={title} />

		<h2 class="text-lg font-semibold mb-2 text-cyan-500">Location</h2>
		<input type="text" class="w-full border rounded px-2 py-1" bind:value={location} />

		<h2 class="text-lg font-semibold mb-2 text-cyan-500">Google Maps URL</h2>
		<input type="text" class="w-full border rounded px-2 py-1" bind:value={googleMapsUrl} />

		<h2 class="text-lg font-semibold mb-2 text-cyan-500">Start Date</h2>
		<input type="text" class="w-full border rounded px-2 py-1" bind:value={startDate} />

		<h2 class="text-lg font-semibold mb-2 text-cyan-500">End Date</h2>
		<input type="text" class="w-full border rounded px-2 py-1" bind:value={endDate} />

		<h2 class="text-lg font-semibold mb-2 text-cyan-500">Description</h2>
		<input type="text" class="w-full border rounded px-2 py-1" bind:value={description} />

		<h2 class="text-lg font-semibold mb-2 text-cyan-500">Image URL</h2>
		<input type="text" class="w-full border rounded px-2 py-1" bind:value={imageUrl} />

		<div class="flex items-center justify-around">
			<button class="text-white rounded mt-2 px-4 py-2 mx-2 bg-cyan-500" on:click={addCard}>
				Add
			</button>

			<button class="mt-2 px-4 py-2 bg-cyan-500 text-white rounded" on:click={() => closeModal()}>
				Close
			</button>
		</div>
	</div>
</div>
