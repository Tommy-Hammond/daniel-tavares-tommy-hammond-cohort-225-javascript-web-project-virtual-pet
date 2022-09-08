<script>
class Pet {
    constructor(name = " ", species = "") {
        // Properties
        this.name = name;
        this.species = species;
        this.hungerStatus = "hungry";
        this.moodQuotient = 5;
        this.mood = calcMood(this.moodQuotient);
        this.birthDay = new Date(Date.now());
        this.age = calcAge(this.birthDay);

        // Methods
        function calcMood(moodQuotient) {
            console.log("moodQuotient: ", moodQuotient)
            const moods = { 
                0: 'FIlled with HATE',
                1: 'Furious',
                2: 'Angry',
                3: 'Frustrated',
                4: 'Upset',
                5: 'Indifferent',
                6: 'Comfortable',
                7: 'Content',
                8: 'Happy',
                9: 'Joyous',
                10: 'Unreasonably Elated'
            }
            return moods[moodQuotient];
        }

        function calcAge(birthDay) {
            let difference = Date.now() - birthDay.getTime();
            let ageDate = new Date(difference);
            console.log({ageDate})
            console.log({difference})
            console.log(Math.abs(ageDate.getUTCFullYear()));
            return Math.abs(ageDate.getUTCFullYear() - 1970);
        }

    }
}

const dog = new Pet("Arlo", "dog");
console.log(dog);
console.log("mood : ", dog.mood);
console.log("age : ", dog.age);
</script>

