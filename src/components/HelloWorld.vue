<template>
  <div class="hello">
    <input type="text" v-model="input">
    <button @click="split(input)">convert</button>
    {{input}}
    {{result}}
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      input: 0,
      result: null
    }
  },
  methods: {
    /**
    * step 1: split the numbers
    * step 2: convert seperate numbers to roman numeral
    * step 2.1: develop logic for numbers 1 to 10
    **** 1: I 2: II 3: III 4: IV 5: V 6: VI 7: VII 8: VIII 9: IX 10: X
    **** 1:I 5:V 10:X 50:L 100:C 500:D 1000:M
    * step 2.2: convert logic to numbers 11 to 9999
    * step 3: add the numeral stings together
    */

    //*************************************************************
    //*********************Splitting the number********************
    //*************************************************************

    split: function(num) {
      let numStr = num.toString()
      let arr = []
      let positions = []
      let arrFin = []
      for (let i of numStr) {
        arr.push(i)
      }
      for(let i = 0; i < arr.length; i++) {
        positions.push((arr.length - 1) - i)
        let zeroLength = (arr.length - 1) - i
        let zero = ''
        for(let e = 0; e <= zeroLength - 1; e++){
          zero += '0'
        }
        arrFin.push(arr[i] + zero )
      }
      /**
      * jede Ziffer bekommt ihrer Position entsprechend viele Nullen:
      *(arr.length - 1) - i
      */
      console.log(arrFin)
      this.result = arrFin
      return 'number: ' + num + ' splitted: ' + arrFin
    }
  },
  computed: {
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
