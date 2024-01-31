<script>
    import { T, useLoader } from '@threlte/core'
    import { TextureLoader, RepeatWrapping, MeshStandardMaterial, sRGBEncoding } from 'three';

    export let pos, sx, sy, sz, col, rot;
    rot = rot !== undefined ? rot : [0,0,0];
    let materials = [];
    let isReady = false;
    let defaultMaterial = new MeshStandardMaterial({ color: col });

    Promise.all([
        useLoader(TextureLoader).load("/textures/stud.png"),
        useLoader(TextureLoader).load("/textures/studnormal.png"),
        useLoader(TextureLoader).load("/textures/inlet.png"), 
        useLoader(TextureLoader).load("/textures/inletnormal.png")
    ]).then(([topTex, topNormal, bottomTex, bottomNormal]) => {
        let textures = [topTex, bottomTex];
        let normals = [topNormal, bottomNormal];
        textures.forEach((tex, index) => {
            let text = tex.clone();
            text.wrapS = RepeatWrapping;
            text.wrapT = RepeatWrapping;
            text.repeat.set(sx, sz);

            let normal = normals[index].clone();
            normal.wrapS = RepeatWrapping;
            normal.wrapT = RepeatWrapping;

            normal.repeat.set(sx, sz);
            materials.push(new MeshStandardMaterial({ map: text, normalMap: normal, color: col }));
        });
        materials = [defaultMaterial, defaultMaterial, materials[0], materials[1], defaultMaterial, defaultMaterial];
        isReady = true;
    });
</script>

{#if isReady}
    <T.Mesh
        position={pos}
        rotation={rot}
        castShadow
        receiveShadow
        material={materials}
    >
        <T.BoxGeometry args={[sx,sy,sz]} />
        <T.Mesh />
    </T.Mesh>
{/if}