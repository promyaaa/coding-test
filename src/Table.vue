<template>
  <div class="app-settings">
    <table>
      <thead>
        <tr>
          <th v-for="column in getColumn()">
            {{ column }}
          </th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in rowdata">
          <td v-for="column in getColumn()">
            {{ item[column] || '' }}
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
<script>
import axios from 'axios';
export default {
  name: 'Test',
  data () {
    return {
      rowdata: [
    
      ]
    };
  },
  methods: {
    getColumn() {
      var result = [];
      this.rowdata.forEach( function( item ){
        Object.keys( item ).forEach( function( col ) {
          if ( result.indexOf( col ) == -1 ) {
            result.push( col );
          }
        })
      });
      return result;
    }
  },
  created() {
    var self = this;
    axios.get(`http://localhost:8080/data/sample.json`)
    .then(response => {
      // JSON responses are automatically parsed.
      self.rowdata = response.data;
      // self.informations = response.data;
      // for(var i=0; i< response.data.length; i++) {
        // uniqueKeys = Object.keys(self.userInfo.reduce(function(result, obj) {
        //   return Object.assign(result, obj);
        // }, {}))
      // }
      // self.header = uniqueKeys;
    });
  }
};
</script>