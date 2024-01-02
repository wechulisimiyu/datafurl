<script>
	import { writable } from 'svelte/store';

	let coords = writable({ x: 50, y: 50 });
	let size = writable(10);
</script>

<!-- <div style="position: absolute; right: 1em;">
	<label>
		<h3>stiffness ({coords.stiffness})</h3>
		<input bind:value={coords.stiffness} type="range" min="0" max="1" step="0.01" />
	</label>

	<label>
		<h3>damping ({coords.damping})</h3>
		<input bind:value={coords.damping} type="range" min="0" max="1" step="0.01" />
	</label>
</div> -->

<svg
    role="button"
    on:mousemove={(e) => coords.set({ x: e.clientX, y: e.clientY })}
    on:mousedown={() => size.set(30)}
    on:mouseup={() => size.set(10)}
    aria-label="Interactive circle"
>
    <circle class="fill-violet" cx={$coords.x} cy={$coords.y} r={$size} role="presentation" aria-hidden="true" />
</svg>

<style>
	svg {
		width: 100%;
		height: 100%;
		margin: -8px;
	}
	/* circle {
		fill: violet;
	} */
</style>
