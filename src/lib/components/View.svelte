<script>
	import { tweened } from "svelte/motion";
	import { cubicOut } from 'svelte/easing';
	
	export let position, rotation;
  	import { HTML } from "@threlte/extras";
	let el;

	let opacity = tweened(0, {
		duration: 100,
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

<HTML transform occlude 
	on:visibilitychange={visChange}
	position={position}>
	<div bind:this={el}>
		<slot />
	</div>
</HTML>