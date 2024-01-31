<script>
	import { T, useLoader } from '@threlte/core'
	import { interactivity, OrbitControls } from '@threlte/extras'
	import { spring } from 'svelte/motion'
	import { TextureLoader, RepeatWrapping, SRGBColorSpace, AmbientLight, DirectionalLight } from 'three';
  	import Part from '../building/Part.svelte';
  	import View from '../components/View.svelte';
</script>
  
<!-- set scene background -->

<T.PerspectiveCamera
	makeDefault
	position={[40, 40, -40]}
	fov={90}
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
	pos={[0,14,-40]}
	sx={20} sy={18} sz={20} 
	col="gray"
/>
<Part 
	pos={[0,24,-40]}
	sx={20} sy={2} sz={20} 
	col="lightgray"
/>
<Part 
	pos={[0,24.5,-20]}
	sx={4} sy={1} sz={20} 
	col="white"
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

<View position={[0,40,0]} rotation={[0,-180,0]}>
	<h1 style="font-size:400px; margin:0;">joblox :3</h1>
	<!-- <h2 style="font-size:100px; margin:0; float:right; background:black;"><a href="https://github.com/nkkls/joblox">src code</a></h2> -->
</View>
<View position={[0,22,10.1]}>
	<div style="border: 3px solid; background-color:black; padding:1em; pointer-events:none;">
		<h1 style="font-size: 50px; margin:0;">scene select</h1>
		<h2 style="font-size: 30px; margin:0;">current scene: main</h2>

	</div>
</View>