<script>
	import { T, useLoader } from '@threlte/core'
	import { TextureLoader, RepeatWrapping, SRGBColorSpace } from 'three';

    export let pos, sx, sy, sz, col;

	let texture;
	let isLoaded = false;
	useLoader(TextureLoader).load("/textures/stud.png").then((tex) => {
        let a = tex.clone();
		a.wrapS = RepeatWrapping;
		a.wrapT = RepeatWrapping;
        a.repeat.set(sx, sz);
		texture = a;
		isLoaded = true;
	});
</script>

{#if isLoaded}
	<T.Mesh
		position={pos}
		castShadow
		receiveShadow
	>
		<T.BoxGeometry args={[sx,sy,sz]} />
		<T.MeshLambertMaterial color={col} map={texture}/>
	</T.Mesh>
{/if}