<script>
	import Model from './Model.svelte'
	let booked = false
	export let name;
	// export let models = ['bob', 'jude', 'jody']

	function selectModel(model) {
		console.log("model selected", model)
	}
	function handleClick(model) {
		console.log("click handled", model)
	}

	export let models = [
		{
			name: "Emilija Papić",
			measurements: {
				height: `5'8"`,
				bust: `34"`,
				waist: `26"`,
				hips: `35"`,
				hair: `brown`,
				eyes: 'brown'
			},
			imageURL: 'http://localhost:8200/app/img/avatars/emilijaHeadshot.jpeg'
		},
		{
			name: "Chloe Kennedy",
			measurements: {
				height: `5'9"`,
				bust: `35"`,
				waist: `27"`,
				hips: `36"`,
				hair: `blond`,
				eyes: 'blue'
			},
			imageURL: 'http://localhost:8200/app/img/avatars/emilijaHeadshot.jpeg'
		},
		{
			name: "Sam Ratajowski",
			measurements: {
				height: `5'11"`,
				bust: `38"`,
				waist: `28"`,
				hips: `37"`,
				hair: `brown`,
				eyes: 'brown'
			},
			imageURL: 'http://localhost:8200/app/img/avatars/emilijaHeadshot.jpeg'
		},
	];
	function bookModel() {
		console.log("booking model")
		fetch('http://3ygun.ngrok.io/send', {method: 'POST'})
		booked = true
	}
</script>

<main class="model-chooser">
	<!--    You have booked Emilija for November 30th from 8am to 11am for Levi's.-->
	{#each models as model, i}
	<div class="model-container">
		<Model model={model}></Model>
	</div>

	{/each}
	<button class="book-now" on:click={bookModel}>Book Now</button>
</main>

<style>
	.book-now {
		border: 0;
		background-color: #edeba2;
		padding: 12px;
		font-weight: bold;
		margin-top: 10px;
	}
	.book-now:hover {
		cursor: pointer;
		background-color: #490399;
		color: white;
	}
	.model-chooser {
		width: 400px;
	}
	.model-container {
		margin-top: 5px;
	}
	main {
		text-align: center;
		padding: 1em;
		/*max-width: 240px;*/
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
