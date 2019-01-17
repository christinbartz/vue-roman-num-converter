<template>
  <div>
    {{checked}}
    <input type="text" v-model="input">
    <button @click="converter(input)" :disabled="!checked">convert</button>
    {{result}}
    {{errorMsg}}
  </div>
</template>

<script>
export default {
  name: 'Converter',
  data () {
    return {
      input: '',
      result: null,
      resource: [['I', 'V', 'X'],['X', 'L', 'C'],['C', 'D', 'M'], ['M']],
      errorMsg: null
    }
  },
  methods: {
    error: function() {
      console.log('error')
    },
    converter: function(num) {
      if(this.checked) {
        let numStr = num.toString()
        let arr
        let arrReversed
        let singles = []
        let convertedReversed = []
        let converted

        // convert number string to an array
        arr = numStr.split('')

        // reverse number array
        arrReversed = arr.reverse()

        // convert numbers to roman counterpart
        for (let num of arrReversed) {
          let converted
          switch(num) {
            case "0":
              converted = ''
              break
            case "1":
              converted = "i"
              break
            case "2":
              converted = "ii"
              break
            case "3":
              converted = "iii"
              break
            case "4":
              converted = "iv"
              break
            case "5":
              converted = "v"
              break
            case "6":
              converted = "vi"
              break
            case "7":
              converted = "vii"
              break
            case "8":
              converted = "viii"
              break
            case "9":
              converted = "ix"
          }
          singles.push(converted)
        }
        // convert the single numbers to their counterparts according to their decimal place
        for (let i = 0; i < singles.length; i++) {
          let converted
          converted = singles[i].replace(/i/g, this.resource[i][0]).replace(/v/g, this.resource[i][1]).replace(/x/g, this.resource[i][2])
          convertedReversed.push(converted)
        }
      converted = convertedReversed.reverse()
      this.result = converted.join('')
      }
    }
  },
  computed: {
    checked: function() {
      if(this.input > 3999) {
        this.errorMsg = "Please enter a number smaller or equal to 3999"
        return false
      } else if (this.input !== '' && /^\d+$/.test(this.input) !== true) {
        this.errorMsg = "Please enter a number"
        return false
      } else {
        this.errorMsg = null
        return true
      }
    }
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
