<script>
  export default {
    data() {
            return {
              count: 10,
              counterTitle: 'Counter Standard',
              incrementAmount: 8,
              message: 'Hello it works',
              listOfNumbers: [
                {
                  id: "Test1",
                  name: "John"
                },
                { 
                  id: "Test2",
                  name: "Jeep"
                },
                { 
                  id: "Test3",
                  name: "James"
                },
                { 
                  id: "Test4",
                  name: "Jim"
                },
                { 
                  id: "Test5",
                  name: "Jay"
                }
              ]
            }
          },
    computed: {
      displayTitle() {
        if(this.count > 20) {
          return 'Counter Standard - Very Long'
        } else {
          return 'Counter Standard'
        }
      },
      optimizedIncrementAmount() {
        return this.displayTitle.length * this.incrementAmount
      }
    },
    methods: {
      incrementCount(newAmount, event){
        this.count += this.optimizedIncrementAmount
      }
    },
    watch: {
      count(newValue){
        if (newValue > 20) {
          this.counterTitle += 'Very Long'
        }
      }
    }
  }
</script>

<template>
 <h1>Hello Frontend Masters!</h1>
    <div id="app">
      <h1>{{ displayTitle }}</h1>
      <p :data-increment-by="incrementAmount">{{ count }}</p>
      <button @click="incrementCount">Increment Count</button>
      <h1>{{ incrementAmount }}</h1>
      <p>{{ optimizedIncrementAmount }} </p>
      <div> 
        <label for="incrementAmount">Increment By:</label>
        <input type="text" v-model="incrementAmount"/>
      </div>
      <hr />
      <p v-if="message.length % 2 ===0">Even: {{ message }}"</p>
      <p v-else>Odd: {{ message }}</p>

      <ul v-for="(item, index) in listOfNumbers" :key="`item-${index}`">
        <li>
          {{ item.id }}
          <ul>
            <li v-for="(number, index) in item.list" :key="`number-${index}`"> 
              {{ number }}
            </li>
          </ul>
        </li>
      </ul>
    </div>
</template>
