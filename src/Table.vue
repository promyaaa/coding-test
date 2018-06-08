<template>
  <div>
    <table>
      <thead>
        <tr>
          <th v-for="column in getColumn()" @click="orderBy(column)">
            {{ column }}
          </th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item, index) in rowdata">
          <td v-for="column in getColumn()">
            <span v-if="editval !== item[column] && editIndex !== index" @click="edit(item, column, index)">{{ item[column] || '' }}</span>
            <span v-if="editval === item[column] && editIndex === index">
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
      editval: -1,
      editIndex: -1,
      editText: ''
    };
  },
  methods: {
    orderBy(p) {
      this.rowdata.sort((a,b) => {
        return (a[p] > b[p]) ? 1 : (a[p] < b[p]) ? -1 : 0;
      });
    },
    cancel() {
      this.editval = -1;
      this.editIndex = -1;
      this.editText = '';
    },
    edit(item, column, index) {
      this.editval = item[column];
      this.editIndex = index;
      this.editText = item[column];
    },
    save( item, column ) {
      item[column] = this.editText;
      this.editval = -1;
      this.editIndex = -1;
      this.editText = '';
      console.log(item[column]);
    },
    getColumn() {
      var result = [];
      this.rowdata.forEach( item => {
        Object.keys( item ).forEach( col => {
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
    .then( response => {
      self.rowdata = response.data;
    });
  }
};
</script>