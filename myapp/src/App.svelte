
<script>
  // @ts-ignore
import svelteLogo from './assets/svelte.svg'
  import VirtualPet from './lib/VPet.svelte'
   import * as PIXI from 'pixi.js'
 import Viewport from './lib/PixiScrn.svelte'
  let name = 'Daniel and Tommy';


</script>

<main> 
  <body>
  
  <div id= "display">
    <Viewport  />
 
  </div>
  
  <div class="card">
    <VirtualPet />
     
 </div>
  
  </body>
</main>

<style>
  * {
    padding:0;
    margin: 0;
    
  }
 
  #display {
  border: 1-x dashed black;
 }

 body {
  height: 90vh;
  display: flex;
  justify-content: center;
  align-items: center;
 }
</style>
