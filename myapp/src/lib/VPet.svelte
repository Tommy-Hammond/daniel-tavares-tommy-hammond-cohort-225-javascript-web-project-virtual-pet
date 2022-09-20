<!-- Example Counter -->
<!-- <script>
  let count = 0
  const increment = () => {
    count += 1
  }
</script>

<button on:click={increment}>
  count is {count}.
</button> -->
<!-- End Example Counter -->


<!-- ------------------------ -->
<!-- Tommy's Code for Pet Class -->
<script>
  export 

  class Pet {

    constructor(name = "Fido") {
      
      this.setName(name);
      this.setHungerQ(5);
      this.setMoodQ(5);

      this.species = this.selectSpecies();
      this.favoriteFood = this.selectFavoriteFood();
      this.favoriteToy = this.selectFavoriteToy();

      this.mood = this.calcMood(this._moodQuotient);
      this.hunger = this.calcHunger(this._hungerQuotient);

      this.dead = false;

      this.initializePet();
      this.setPrintableList();

    }

    //Setters and Getters
    setName(newName) {
        //newName = newName.trim();
        if (newName === '') {
          throw 'Name cannot be empty';
        }
        this.name = newName;
        this.setPrintableList();
    }

    getName() {
      return this.name;
    }

    setHungerQ(newHungerQuotient) {
      this._hungerQuotient = newHungerQuotient;
      this.setPrintableList();
    }

    getHungerQ() {
      return this._hungerQuotient;
    }

    setMoodQ(newMoodQuotient) {
      this._moodQuotient = newMoodQuotient;
      this.setPrintableList();
    }

    getMoodQ() {
      return this._moodQuotient;
    }

    setPrintableList() {
      this.printableList = {
        name: this.name,
        species: this.species,
        hunger: this.hunger,
        mood: this.mood,

        //Temporarily printable
        favoriteFood: this.favoriteFood,
        favoriteToy: this.favoriteToy,
        hungerQ: this._hungerQuotient,
        moodQ: this._moodQuotient

      };

      //Update Storage
      localStorage.setItem('virtualPet', JSON.stringify(this));

      //Update death
      if (this.dead) {
        this.death();
        this.printableList = {
          'In a better place' : this.name
        }
      }

    }

    //Methods
    initializePet() {
      let tempPet = JSON.parse(localStorage.virtualPet);
      console.log('From storage : ', tempPet);
      for (const prop in tempPet) {
        console.log('setting now: ', this[prop] = tempPet[prop]);
      }
    }

    getRandomInt(max) {
      return Math.floor(Math.random() * max);
    }

    selectSpecies() {
      let random = this.getRandomInt(4);
      const species = {
        0: 'Dog',
        1: 'Cat',
        2: 'Lobster',
        3: 'Onion'
      }
      this.setPrintableList();
      return species[random];
    }

    selectFavoriteFood() {
      let random = this.getRandomInt(4);
      const foods = {
        0: 'Taco',
        1: 'Peanutbutter',
        2: 'Lobster',
        3: 'Onion'
      }
      this.setPrintableList();
      return foods[random];
    }

    selectFavoriteToy() {
      let random = this.getRandomInt(3);
      const toys = {
        0: 'Ball',
        1: 'Shoe',
        2: 'Matches'
      }
      this.setPrintableList();
      return toys[random];
    }

    calcMood(_moodQuotient) {
      const moods = { 
        0: 'filled with HATE',
        1: 'furious',
        2: 'angry',
        3: 'frustrated',
        4: 'upset',
        5: 'indifferent',
        6: 'content',
        7: 'happy',
        8: 'jolly',
        9: 'joyous',
        10: 'unreasonably elated'
      }
      this.setPrintableList();
      return moods[_moodQuotient];
    }

    calcHunger(_hungerQuotient) {
      const hungerStatus = { 
        0: 'on the brink of death',
        1: 'starving',
        2: 'hangry',
        3: 'hungry',
        4: 'snacky',
        5: 'Indifferent',
        6: 'satisfied',
        7: 'full',
        8: 'very full',
        9: 'painfully full',
        10: 'wanting to end it all'
        }
        this.setPrintableList();
      return hungerStatus[_hungerQuotient];
    }

    feed(food) {
      if (food == this.favoriteFood && this._moodQuotient < 10) {
        this._moodQuotient += 1;
        //this.mood = this.calcMood(this._moodQuotient);
      }

      if (this._hungerQuotient == 10 && this._moodQuotient > 0) {
        this._moodQuotient -= 1;
        //this.mood = this.calcMood(this._moodQuotient);
        //return this.hunger;
      }
      else {
        this._hungerQuotient += 1;
        //this.hunger = this.calcHunger(this._hungerQuotient);
      }

      this.mood = this.calcMood(this._moodQuotient);
      this.hunger = this.calcHunger(this._hungerQuotient);
      this.setPrintableList();
    }

    play(toy) {
      if (toy == this.favoriteToy && this._moodQuotient < 9) {
        this._moodQuotient += 2;
      }
      else if (this._moodQuotient < 10) {
        this._moodQuotient += 1;
      }

      if (this._hungerQuotient == 0) {
        this.dead = true;
      }
      if (this._hungerQuotient > 0) {
        this._hungerQuotient -= 1;
      }

      this.hunger = this.calcHunger(this._hungerQuotient)
      this.mood = this.calcMood(this._moodQuotient);
      this.setPrintableList();
    }

    death() {
      localStorage.clear();
    }


  }

  function checkPet() {
    if (localStorage.virtualPet) {
      // const pet1 = new Pet();
      //pet1.initializePet();
      const tempPet = new Pet();
      tempPet.initializePet();
      return tempPet;
    }
    else {
      return new Pet('Gazpacho');
    }
  }

// if (localStorage.virtualPet) {
//   const pet1 = JSON.parse(localStorage.getItem('virtualPet'));
//   pet1.setPrintableList();
//   console.log('Old Pet: ', pet1)
//  }
// else {
//   const pet1 = new Pet('Gazpacho');
//   console.log('New Pet: ', pet1)
//   pet1.setPrintableList();
//  }

//Testing

  // pet1.getMoodQ();
  // pet1.getHungerQ();
  // pet1.feed('Lobster');

  // pet1.getMoodQ();
  // pet1.getHungerQ();
  // pet1.feed('Onion');

  // pet1.getMoodQ();
  // pet1.getHungerQ();
  // pet1.feed('Taco');

  // pet1.getMoodQ();
  // pet1.getHungerQ();
  // pet1.play('Ball');

  // pet1.getMoodQ();
  // pet1.getHungerQ();
  const pet1 = checkPet();

  pet1.play('Ball');
  pet1.play('Ball');
  pet1.feed('Lobster');
  pet1.play('Ball');
  pet1.play('Ball');
  pet1.play('Matches');




</script>

{#each Object.entries(pet1.printableList) as [key, value]}
  <h3>{key}: {value}</h3>
{/each}                    

<!-- End of Tommy's Code for Pet Class -->



