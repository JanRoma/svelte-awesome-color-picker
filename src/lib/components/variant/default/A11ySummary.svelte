<script lang="ts">
	import type { A11yColorContract } from '$lib/type/types';

	export let a11yColors: Array<A11yColorContract>;
	/* svelte-ignore unused-export-let */
	export let hex: string;

	function getNumberOfGradeFailed({ contrast, size }: A11yColorContract): number {
		if (!contrast) {
			return 1;
		}
		if (size === 'large') {
			return contrast < 3 ? 2 : contrast < 4.5 ? 1 : 0;
		} else {
			return contrast < 4.5 ? 2 : contrast < 7 ? 1 : 0;
		}
	}

	$: count = a11yColors.map(getNumberOfGradeFailed).reduce((acc, c) => acc + c);

	$: message = count
		? `⚠️ ${count} contrast grade${count && 's'} fail`
		: 'Contrast grade information';
</script>

{message}
