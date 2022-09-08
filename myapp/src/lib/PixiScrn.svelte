<script>
import { attribute_to_object } from "svelte/internal";

const Application = PIXI.Application;

const app = new Application({
  width: 500,
  height: 500,
  backgroundColor: 0xF8F8F8
});

app.renderer.resize(window.innerWidth,window.innerHeight);

app.renderer.view.style.position = 'absolute';

document.body.appendChild(app.view);



const container = new PIXI.Container();

app.stage.addChild(container);

//const PetTexture1 = PIXI.Texture.from('https://i.postimg.cc/GpYDWcRX/New-Piskel-1-png.png');
//const PetSprite1 = new PIXI.Sprite(PetTexture1);

const PetSprite1 = PIXI.Sprite.from('https://i.postimg.cc/GpYDWcRX/New-Piskel-1-png.png');

app.stage.addChild(PetSprite1);

PetSprite1.anchor.set(0.5,0.5);
PetSprite1.scale.set(10,10);
PetSprite1.position.set(800,300);

</script>