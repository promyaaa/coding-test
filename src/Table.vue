<template>
  <div>
    <table>
      <thead>
        <tr>
          <th v-for="column in getColumn()">
            {{ column }}
          </th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item, index) in rowdata">
          <td v-for="column in getColumn()" >
            <span v-if="editindex !== item[column]" @click="edit(item, column, index)">{{ item[column] || '' }}</span>
            <span v-if="editindex === item[column]">
              <input type="text" v-model="editText">
              <button @click="save(item, column, index)">save</button>
              <button @click="cancel">cancel</button>
            </span>
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
      rowdata: [],
      editindex: -1,
      editText: '',
    };
  },
  methods: {
    cancel() {
      this.editindex = -1;
      this.editText = '';
    },
    edit(item, column, index) {
      this.editindex = item[column];
      this.editText = item[column];
    },
    save( item, column ) {
      item[column] = this.editText;
      this.editindex = -1;
      this.editText = '';
    },
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
      self.rowdata = response.data;
    });
  }
};
</script>