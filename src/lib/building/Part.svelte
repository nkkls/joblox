<script>
	import { T, useLoader } from '@threlte/core'
	import { TextureLoader, RepeatWrapping, MeshLambertMaterial, sRGBEncoding} from 'three';

    export let pos, sx, sy, sz, col;

	let materials = [];
	let defaultMaterial = new MeshLambertMaterial({ color: col })
    let isReady = false;
    Promise.all([
        useLoader(TextureLoader).load("/textures/stud.png"),
        useLoader(TextureLoader).load("/textures/inlet.png")
    ]).then(([topTex, bottomTex]) => {
        [topTex, bottomTex].forEach(tex => {
            let a = tex.clone();
            a.wrapS = RepeatWrapping;
            a.wrapT = RepeatWrapping;
			a.encoding = sRGBEncoding;
            a.repeat.set(sx, sz);
            materials.push(new MeshLambertMaterial({ map: a , color: col}));
        });
        materials = [defaultMaterial,defaultMaterial, materials[1],materials[0],defaultMaterial,defaultMaterial];
        isReady = true;
    });
</script>

{#if isReady}
	<T.Mesh
		position={pos}
		castShadow
		receiveShadow
		material={materials}
	>
		<T.BoxGeometry args={[sx,sy,sz]} />
	</T.Mesh>
{/if}