<script>
	export let model = {
		// name: "Emilija Papic'",
		// measurements: {
		//   height: `5'8"`,
		//   bust: `34"`,
		//   waist: `26"`,
		//   hips: `35"`,
		//   hair: `brown`,
		//   eyes: 'brown'
		// },
		// imageURL: 'http://localhost:8200/app/img/avatars/emilijaHeadshot.jpeg'
	};
	$: console.log(model)
	let measurementKeys
	let lastMeasurementKey
	$: {
		if (model.measurements) {
			measurementKeys = Object.keys(model.measurements)
			lastMeasurementKey = measurementKeys.pop()
		}
	}
	let clicked = false
	console.log('meausermentKeys is ', measurementKeys)
	export let onclick = function() {
		clicked = !clicked

	}
	let klass = 'new-booking-talent-selection-list-item'
	$: {
		if (clicked) {
			klass =  'new-booking-talent-selection-list-item new-booking-talent-selection-list-item-selected'
		}
	}
</script>
<li on:click={onclick} class={klass}>
	<div class="new-booking-talent-selection-list-img-container">
		<img src={model.imageURL} class="new-booking-talent-selection-list-img">
	</div>
	<div class="new-booking-talent-selection-list-item-info">
		<div class="new-booking-talent-selection-list-item-info-name">
			{model.name}
		</div>
		<div class="new-booking-talent-selection-list-item-info-measurements" >
			<!--      {measurementKeys && measurementKeys.length}-->
			{#if measurementKeys}
			{#each measurementKeys as key}
			<span class="measurementKey">{key}</span>: <span class="measurementValue">{model.measurements[key]} <span class="divider">•</span> </span>
			{/each}
			{/if}
			{#if lastMeasurementKey}
			<span class="measurementKey">{lastMeasurementKey}</span>: <span class="measurementValue">{model.measurements[lastMeasurementKey]}</span>
			{/if}
		</div>
	</div>
</li>
<style>
	/* edeba2 */
	.new-booking-body {
		display: flex;
		flex-direction: row;
		width: 100%;

	}
	.new-booking-event-info {
		flex: 50;
	}
	.new-booking-talent-selection {
		flex: 50;
	}
	.new-booking-talent-selection-header {
	}
	.new-booking-talent-selection-list {

	}
	.new-booking-talent-selection-list-item {
		display: flex;
		padding: 4px;
		align-items: center;
	}

	.new-booking-talent-selection-list-item-info-name {
		text-align: left;
		padding-bottom: 4px;
		text-transform: uppercase;
		color: #490399;
	}

	.new-booking-talent-selection-list-item-info-measurements {
		text-align: left;

	}
	.new-booking-talent-selection-list-item:hover {
		cursor: pointer;
		background-color: palegoldenrod;
	}
	.new-booking-talent-selection-list-item-selected {
		background-color: palegoldenrod;
	}
	.new-booking-talent-selection-list-img-container {
		width: 90px;
		height: 90px;
		padding-right: 20px;
		align-items: center;
		display: flex;

	}
	.new-booking-talent-selection-list-img {
		max-width: 100%;
		max-height: 100%;
	}
	.new-booking-client-label {

	}
	.new-booking-client-input {

	}
	.measurementKey {
		text-transform: uppercase;
		font-size: small;
		color: #56626b;
	}
	.measurementValue {
		font-size: small;
	}
	.divider {
		font-size: small;
		padding-left: 4px;
		padding-right: 4px;
	}

</style>

