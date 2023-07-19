<script>
	import { store } from '../lib/store.js';
	import CardDetails from '../components/CardDetails.svelte';
	let sidebarOpen = false;
	let selectedCard = null;


	let searchText = '';


	function toggleSidebar() {
		sidebarOpen = !sidebarOpen;
	}

	function selectCard(card) {
		selectedCard = card;
	}
</script>

<div class="relative flex min-h-screen">
	<div
		class="bg-cyan-600 text-cyan-100 w-64 space-y-6 px-2 py-4 absolute inset-y-0 left-0 md:relative md:-translate-x-0 transform -translate-x-full transition duration-200 ease-in-out {sidebarOpen
			? 'relative translate-x-0'
			: ''}"
	>
		<a href="/" class="flex items-center space-x-2 px-4"
			><svg
				width="24"
				height="24"
				viewBox="0 0 24 24"
				fill="none"
				xmlns="http://www.w3.org/2000/svg"
				class="w-9 h-8 m-1"
			>
				<path
					fill-rule="evenodd"
					clip-rule="evenodd"
					d="M19.8649 17.2C19.7357 17.0799 19.6376 16.9553 19.6044 16.84C19.4739 16.383 19.646 15.0548 19.9048 14.6401C20.1628 14.2239 19.877 12.975 19.7926 12.7683C19.7058 12.5604 19.6767 12.2906 19.3805 12.3724C19.0826 12.4558 18.4132 12.4247 17.8078 12.3002C17.2008 12.1768 16.6723 11.5921 16.5514 10.9328C16.416 10.1937 16.416 9.47567 16.5888 9.02547C16.782 8.5194 17.2577 8.32783 17.6932 8.08917C17.8938 7.97981 18.8644 7.82496 18.8279 7.358C18.6023 6.92776 16.5418 7.41707 16.4592 6.74856C16.3756 6.07886 16.3461 5.74281 16.6075 5.20401C16.8817 4.64207 16.5664 4.7171 16.4907 4.03583C16.4804 3.93884 16.6952 3.6882 16.7122 3.6C17.4231 4.0043 18.0908 4.48762 18.6899 5.06313C20.5667 6.8667 21.6 9.26454 21.6 11.8152C21.6 13.7669 20.9905 15.6255 19.8649 17.2ZM15.4437 16.8971C15.034 17.5476 15.1325 18.0268 14.1978 18.5241C13.6772 18.8014 13.3068 18.88 13.0314 19.6248C12.7548 20.368 12.2962 20.3418 11.1513 20.9456C10.0047 21.5509 9.54928 20.9456 9.45589 20.4813C9.36289 20.017 9.64545 18.9203 9.64545 18.9203C9.64545 18.9203 9.75752 18.5927 8.94521 18.2227C6.89098 17.2872 8.66344 14.0029 8.66344 14.0029C8.19926 13.4596 7.02053 12.394 5.37484 12.045C3.80148 11.7121 3.3528 10.7887 2.8 9.867C3.20457 8.16055 4.05464 6.59235 5.30967 5.31877C7.10479 3.49786 9.49086 2.4 12.0315 2.4C12.0315 2.4 12.8883 2.4 13.6971 2.6124C12.9575 3.42653 12.1301 4.24952 11.5153 4.47643C10.4085 4.88752 9.89543 5.56099 9.89066 6.27839C9.88827 6.64999 10.6577 7.32345 10.6577 8.17547C10.6577 9.62356 9.59498 9.65702 9.47099 9.04682C9.19121 7.66281 8.12097 8.0203 6.83931 8.15894C5.55567 8.29879 4.77793 9.81017 5.60216 10.4147C6.42799 11.0193 6.38547 10.2237 6.703 9.99677C7.01894 9.76946 7.24229 9.67959 7.48233 9.99677C7.72038 10.314 8.23662 10.4865 8.18694 11.1374C8.14363 11.7879 8.00453 12.3448 8.87685 12.3448C9.74799 12.3448 9.77819 12.5391 10.331 12.8176C10.8782 13.0965 11.3965 13.0441 11.8531 13.1376C12.3117 13.2299 12.9126 14.1279 12.9126 14.1279C14.2125 14.5539 14.6401 14.728 14.999 15.0907C15.3567 15.4534 15.8582 16.2462 15.4437 16.8971ZM11.9986 0H11.9954H11.9922C7.23149 0 3.13019 2.7812 1.19038 6.8C0.430136 8.3748 8.94955e-08 10.1344 8.94955e-08 12C-0.000800164 18.6264 5.3653 24 11.9938 24H11.997H12.0002C18.6263 24 24.0008 18.6264 24 12.0016C24.0008 5.314 18.5467 0 11.9986 0Z"
					fill="white"
				/>
			</svg><span class="text-2xl font-extrabold text-white">Travel Diary</span>
		</a>
		<nav>
			<input
				class="bg-cyan-500 appearance-none border-2 border-cyan-200 rounded w-full py-2 px-4 text-gray-700 placeholder-gray-700 focus:outline-none focus:bg-white focus:border-cyan-300"
				type="text"
				placeholder="Search"
				bind:value={searchText}
			/>
			{#each $store as card (card.id)}
				<a
					on:click={() => selectCard(card)}
					href="/"
					class="group flex items-center space-x-2 py-3 px-4 my-2 hover:bg-cyan-700 rounded-md hover:text-cyan-300 transition duration-200"
					><svg
						class="h-6 w-6"
						xmlns="http://www.w3.org/2000/svg"
						fill="none"
						viewBox="0 0 24 24"
						stroke-width="1.5"
						stroke="currentColor"
					>
						<path stroke-linecap="round" stroke-linejoin="round" d="M8.25 4.5l7.5 7.5-7.5 7.5" />
					</svg>
					<span class="text-white group-hover:text-cyan-300">{card.title}</span>
				</a>
			{/each}
			<button
				class="space-x-2 py-3 px-4 bg-cyan-300 border-2 w-full rounded text-cyan-700 hover:text-cyan-300 border-cyan-200 flex justify-center my-4 hover:bg-cyan-600 transition duration-200"
				><svg
					xmlns="http://www.w3.org/2000/svg"
					fill="none"
					viewBox="0 0 24 24"
					stroke-width="1.5"
					stroke="currentColor"
					class="w-7 h-7"
				>
					<path stroke-linecap="round" stroke-linejoin="round" d="M12 4.5v15m7.5-7.5h-15" />
				</svg>
			</button>
		</nav>
	</div>

	<div class="flex-1">
		<div class="bg-white shadow px-2 py-4 flex justify-start items-center">
			<button on:click={toggleSidebar} class="text-cyan-600 font-extrabold flex-shrink-0"
				><svg
					xmlns="http://www.w3.org/2000/svg"
					fill="none"
					viewBox="0 0 24 24"
					stroke-width="1.5"
					stroke="currentColor"
					class="w-8 h-8"
				>
					<path
						stroke-linecap="round"
						stroke-linejoin="round"
						d="M3.75 6.75h16.5M3.75 12h16.5m-16.5 5.25h16.5"
					/>
				</svg>
			</button>
			<h1 class="flex-grow flex justify-center font-extrabold text-2xl text-cyan-600">
				Travel Diary
			</h1>
			<a href="/page2" class="font-normal text-2xl text-cyan-600">
				Next Page
			</a>
		</div>

		<div class="p-8 text-cyan-700 font-extrabold">
			<CardDetails {...selectedCard} />
		</div>
	</div>
</div>
