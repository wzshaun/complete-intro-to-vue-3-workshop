<script>
  export default {
    data: () => ({
      newCharacter: {
        name: '',
        element: []
      },
      characterList: [
        {
          name: 'Aang',
          element: ['Air', 'Earth', 'Water', 'Fire']
        }, {
          name: 'Zuko',
          element: ['Fire']
        }, {
          name: 'Toph',
          element: ['Earth']
        }, {
          name: 'Katara',
          element: ['Water']
        } 
      ],
      favouriteList: [], // Corrected spelling here
      listOfNumbers: [1, 2, 3, 4, 5]
    }),
    computed: {
      benderStatistics() {
        const elements = ['Air', 'Earth', 'Fire', 'Water']

        const statistics = {
          Air: 0,
          Earth: 0,
          Water: 0,
          Fire: 0
        }

        this.characterList.forEach(character => {
          elements.forEach(element => {
            if (character.element.indexOf(element) > -1) {
              statistics[element] += 1
            }
          })
        })

        return statistics
      }
    },
    methods: {
      addNewCharacter() {
        this.characterList.push(this.newCharacter);
        this.newCharacter = { name: '' };
      },
      favouriteCharacter(character) {
        this.favouriteList.push(character); // Corrected spelling here
      }
    }
  }
</script>

<template>
     <div id="app">
      <h2>Statistics</h2>
      <ul>
        <li v-for="(stat, type) in benderStatistics"> {{type}}:{{stat}}</li>
        <!-- <li>Earth: {{ earthBenderList }}</li>
        <li>Water:</li>
        <li>Fire:</li>
        <li>Air:</li> -->
      </ul>
      <h2>Characters</h2>
      
      <p v-if="characterList.length === 0"> there are no character</p>
      <ul>
        <li v-for="character in characterList">
          <p>{{ character.name }}</p>
          <button @click="favouriteCharacter(character)">Favourite</button>
        </li>
      </ul>

      <h2>Favourite Characters</h2>
      <ul v-if="favouriteList.length > 0">
        <li v-for="character in favouriteList">{{ character }}</li>
      </ul>
      <p v-else>No Favourite Characters Yet!</p>
      <p v-else>There are odd characters!</p>
      <h2>New Character</h2>
      <pre> {{newCharacter }}</pre>
      <label for="character-name">Name</label>
      <input
        type="text"
        v-model="newCharacter.name"
        @keyup.enter="addNewCharacter"
      />
      <p>
        <span v-for="(character, index) in characterList">
          {{ character.name }}{{ index === characterList.length - 1 ? '' : ', ' }}
        </span>
      </p>
    </div>
 </template>

