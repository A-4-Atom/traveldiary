<script>
	export let title;
	export let location;
	export let googleMapsUrl;
	export let startDate;
	export let endDate;
	export let description;
	export let imageUrl;
</script>

{#if title}
	<div class="bg-white rounded-lg shadow-md overflow-hidden">
		<img class="w-full h-48 object-cover bg-cover" src={imageUrl} alt={title} />

		<div class="p-4 text-cyan-600">
			<h3 class="text-lg font-semibold text-cyan-600">{title}</h3>
			<p class="mb-2 text-cyan-600">{location}</p>
			<p class="text-cyan-600 mb-2 font-normal">{startDate} - {endDate}</p>
			<p class="text-gray-800 font-normal text-lg">{description}</p>
			<a
				href={googleMapsUrl}
				target="_blank"
				rel="noopener noreferrer"
				class="text-blue-500 hover:underline"
			>
				View on Google Maps
			</a>
		</div>
	</div>
{:else}
	<div class="bg-white p-4 shadow-md rounded">
		<h2 class="text-2xl font-semibold">No Card Selected</h2>
	</div>
{/if}
