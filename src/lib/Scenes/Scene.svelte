<script>
	import { T, useLoader } from '@threlte/core'
	import { interactivity, OrbitControls } from '@threlte/extras'
	import { spring } from 'svelte/motion'
	import { TextureLoader, RepeatWrapping, SRGBColorSpace, AmbientLight, DirectionalLight } from 'three';
  	import Part from '../building/Part.svelte';
  import View from '../components/View.svelte';

	let texture, texture2;
	useLoader(TextureLoader).load("/textures/stud.png").then((tex) => {
		tex.wrapS = RepeatWrapping;
		tex.wrapT = RepeatWrapping;
		tex.repeat.set(200,200);
		tex.colorSpace = SRGBColorSpace
		texture = tex;
	})

</script>
  
<!-- set scene background -->

<T.PerspectiveCamera
	makeDefault
	position={[10, 5, 0]}
	fov={90}
	on:create={({ ref }) => {
		ref.lookAt(0, 4, 0)
	}}
>
	<OrbitControls enableDamping />
</T.PerspectiveCamera>

<T.AmbientLight 
	color="lightgray"
/>
<!-- add direction and target -->
<T.DirectionalLight 
	color="white"
	position={[0, 10, 0]}

/>

<Part 
	pos={[0,0,0]}
	sx={200} sy={10} sz={200} 
	col="gray"
/>

<Part 
	pos={[0,15,0]}
	sx={20} sy={20} sz={20} 
	col="lightgray"
/>

<Part 
	pos={[20,10,0]}
	sx={20} sy={10} sz={20} 
	col="lightgray"
/>

<Part 
	pos={[13,18,0]}
	sx={6} sy={6} sz={6} 
	col="orange"
/>

<Part 
	pos={[33,8,0]}
	sx={6} sy={6} sz={6} 
	col="lightblue"
/>

<!-- <View position={[-10,40,0]}>
	<iframe width="1024" height="768" src="https://niko.pages.gay" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</View> -->
<!-- <View position={[30,40,0]}>
	<h1 style="font-size:400px">joblox :3</h1>
</View> -->
<!-- <View position={[-10,80,0]}>
	<h1 style="font-size:400px">joblox :3</h1>
</View> -->