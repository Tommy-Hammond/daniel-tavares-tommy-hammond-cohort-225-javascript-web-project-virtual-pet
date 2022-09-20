<script>
  //import svelteLogo from './assets/svelte.svg'
  import PetModule , {} from './lib/VPet.svelte'
  //import PetModule2 from './lib/VPet2.svelte'

  let name = 'Daniel and Tommy';
  </script>

<main>
  
<div class="petstylingapp stack-large">
  <h1>{name}</h1>
  <div><PetModule /></div>
  <!-- Filter -->
  <div class="filters btn-group stack-exception">


    <button class="btn" on:click={pet1.play("ball")} >
      <span class="visually-hidden">Press to</span>
      <span>Play</span>
      <span class="visually-hidden">with your pet</span>
    </button>
    
    
    <button class="btn">
      <span class="visually-hidden">Press to</span>
      <span>Feed</span>
      <span class="visually-hidden">your Pet</span>
    </button>
   
  </div>

  <!-- Pet Status -->
  <h2 id="list-heading"><img src="https://wc.wallpaperuse.com/wallp/85-854941_s.jpg" >  </h2>

  <!-- -->
  <ul role="list" class="petstyling-list stack-large" aria-labelledby="list-heading">
    <!-- petstyling-1 (editing mode) -->
    <li class="petstyling">
      <div class="stack-small">
        <form class="stack-small">
          <div class="form-group">
            <label for="petstyling-1" class="petstyling-label">
              New name
            </label>
            <input
              type="text"
              id="petstyling-1"
              autocomplete="off"
              class="petstyling-text" />
          </div>
          <div class="btn-group">
            <button class="btn btn__primary petstyling-edit" type="submit">
              Save
              <span class="visually-hidden">new name for your Pet</span>
            </button>
          </div>
        </form>
      </div>
    </li>

   
  </ul>
  

</main>


