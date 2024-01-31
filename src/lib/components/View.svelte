<script>
	import { tweened } from "svelte/motion";
	import { cubicOut } from 'svelte/easing';

  	import { HTML } from "@threlte/extras";
	let el;

	let opacity = tweened(1, {
		duration: 200,
		easing: cubicOut
	})
    const visChange = (isVisible) => {
		// smoothly change opacity and display
		opacity.set(isVisible ? 1 : 0);
  	}

	opacity.subscribe((value) => {
        if (el && el.style) {
            el.style.opacity = value;
        }
    });
</script>

<HTML transform occlude castShadow
	on:visibilitychange={visChange}
	{...$$restProps}>
	<div bind:this={el}>
		<slot />
	</div>
</HTML>