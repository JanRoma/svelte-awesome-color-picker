<script lang="ts">
	export let pos: { x: number; y: number };
	/* svelte-ignore unused-export-let */
	export let hex: string;
	export let isDark: boolean;

	$: left = `calc(${pos.x} * (var(--picker-width, 260px) - 14px) / 100 + 2px)`;
	$: top = `calc(${pos.y} * (var(--picker-height, 200px) - 14px) / 100 + 2px)`;
</script>

<div
	class="picker-indicator"
	style={`left: ${left}; top: ${top}; box-shadow: 0 0 4px ${isDark ? 'white' : 'black'};`}
/>

<style>
	div {
		position: absolute;
		width: 10px;
		height: 10px;
		background-color: white;
		border-radius: 5px;

		pointer-events: none;
		z-index: 1;
		transition: box-shadow 0.2s;
	}
</style>
