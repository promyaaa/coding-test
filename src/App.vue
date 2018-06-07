<!-- <template>
    <div id="app">
      <h1>Table Component</h1>
      <table style="width:100%">
  <tr v-for="h in header">
    <th>{{h}}</th>
  </tr>
  <tr v-for="info in informations">
    <td>{{info.first_name}}</td>
    <td>Smith</td> 
    <td>50</td>
  </tr>
  <tr>
    <td>Eve</td>
    <td>Jackson</td> 
    <td>94</td>
  </tr>
</table>
      <pre>
      {{header}}
      </pre>
    </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'app',
  data () {
    return {
      informations:[],
      sampleOne: [{ "first_name": "Billy", "last_name": "Campbell", "phone": "62-(500)527-5325" }, { "first_name": "Jonathan", "last_name": "Black", "country": "Russia", "phone": "7-(729)811-4597" }, { "first_name": "cheryl", "last_name": "Harvey", "country": "Indonesia", "phone": "62-(825)454-3810" }, { "first_name": "Cynthia", "last_name": "Cooper" }, { "first_name": "Thomas", "last_name": "Stevens", "phone": "86-(527)535-8464" }, { "first_name": "Jane", "last_name": "Chavez", "country": "Netherlands" }, { "first_name": "bobby", "last_name": "Price", "country": "China", "phone": "86-(898)723-6749" }, { "first_name": "Steve", "last_name": "Hansen", "phone": "93-(362)494-5552" }, { "first_name": "Alan", "last_name": "Cruz", "country": "Philippines", "phone": "63-(617)248-8832" }, { "first_name": "Dennis", "last_name": "Baker", "country": "Iran", "phone": "98-(436)329-3723" }, { "first_name": "Ernest", "last_name": "Bishop", "phone": "86-(566)429-1138" }, { "first_name": "Russell", "last_name": "Meyer", "phone": "62-(687)827-4302" }, { "first_name": "Ryan", "last_name": "Mendoza", "country": "Poland", "phone": "48-(537)109-0373" }, { "first_name": "Maria", "last_name": "Greene", "phone": "92-(831)367-8049" }, { "first_name": "Elizabeth", "last_name": "Moore", "country": "Philippines", "phone": "63-(694)844-9255" }, { "first_name": "Ronald", "last_name": "kim", "phone": "46-(339)931-9221" }, { "first_name": "Samuel", "last_name": "Jacobs", "country": "Russia", "phone": "7-(936)156-5229" }, { "first_name": "Fred", "last_name": "Ross", "phone": "55-(594)481-7354" }, { "first_name": "Andrew", "last_name": "Burns", "country": "Portugal", "phone": "351-(174)443-8706" }, { "first_name": "Robert", "last_name": "Frazier", "country": "Somalia" }],
      userInfo: [],
      header: []
    }
   },
   computed: {
    
   },
  created() {
    var uniqueKeys;
    var self = this;
    axios.get(`http://localhost:8080/data/sample.json`)
    .then(response => {
      // JSON responses are automatically parsed.
      self.userInfo = response.data;
      self.informations = response.data;
      // for(var i=0; i< response.data.length; i++) {
        uniqueKeys = Object.keys(self.userInfo.reduce(function(result, obj) {
          return Object.assign(result, obj);
        }, {}))
      // }
      self.header = uniqueKeys;
    })
    .catch(e => {
      
    })
  }
}
</script>

<style>

</style>
 -->