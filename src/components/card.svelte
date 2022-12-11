<script>
	export let title;
	// export let image;
	// export let description;?
	export let action;
	export let disabled;
</script>

<div on:click={action} {disabled} aria-hidden="true">
	<h5>{title}</h5>
</div>

<style>
	div {
		background-color: aquamarine;
		border-radius: 12px;
	}
	div:disabled {
		background-color: gainsboro;
	}
</style>
