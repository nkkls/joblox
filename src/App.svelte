<script>
  import { Canvas, useLoader, useThrelte} from '@threlte/core'
  import { Environment } from '@threlte/extras';
  import Scene from './lib/Scenes/Scene.svelte';

  let path = "/skyboxes/Sunny Sky/"
  let files = ["2.png", "4.png", "5.png", "6.png", "1.png", "3.png"]
  
</script>

<Canvas>
  <Environment {path} {files} isBackground="true" />
  <Scene />
</Canvas>
