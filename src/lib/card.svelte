<script lang="ts">
	import { Motion } from "svelte-motion"
	export let num: number
	export let selected: number | undefined

	const onClick = () => selected = selected === num ? undefined : num
</script>

{#if selected === undefined || selected === num}
	<Motion let:motion={m1} layout layoutId="key-{num}">
		<section use:m1 class:selected={selected === num} on:click={onClick} style:--grid-start={num} style:--grid-end={num + 1}>
			<Motion let:motion={m2} layout layoutId="key-{num}-child">
				<div use:m2>
					<slot />
				</div>
			</Motion>
		</section>
	</Motion>
{/if}

<style>
	section {
		width: 100%;
		height: 100%;
		background: var(--color, white);
		grid-column: var(--grid-start, auto) / var(--grid-end, auto);
		grid-row: 1 / 2;
	}

	.selected {
		grid-column: 1 / -1;
	}

	section div {
		width: max-content;
	}
</style>
