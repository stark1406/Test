<template>
<div style="display: flex; justify-content: center;">
  <div class="table-container">
    <table>
      <thead>
        <tr>
          <th :style="styleColumn">#</th>
          <th v-for="(column, index) in columns" :key="index" :style="styleColumn">
            {{ column }}
          </th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(row, rowIndex) in rows" :key="rowIndex">
          <td :style="styleRow">{{ rowIndex + 1 }}</td>
          <td :style="styleTd"
            v-show="check"
            v-for="(data, columnIndex) in row.data"
            :key="columnIndex"
          >
            <input  style="width: 60px" maxlength="6" :value="data.value" />
          </td>
          <td :style="styleTd" v-show="!check" v-for="column in columns">
            <div class="icon-container">
              <img src="../assets/logo.png" height="25px" width="25px" alt="icon" />
            </div>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</div>
</template>

<script>
export default {
  name: "Table",
  props: {
    columns: {
      type: Array,
      default: () => [],
    },
    rows: {
      type: Array,
      default: () => [],
    },
    check: Boolean,
  },
  computed: {
    styleColumn() {
        return this.check ? 'background: #fffead' : 'background: aqua'
    },
    styleRow() {
        return this.check ? 'background: #fffead' : 'background: aqua'
    },
    styleTd() {
        return this.check ? 'background: aqua' : 'background: #fffead'
    },
  }
};
</script>

<style lang="scss">
.table-container {
  max-height: 500px;
  overflow: auto;
  max-width: 1000px;
  table {
    width: 1000px;
    height: 500px;
    border-collapse: collapse;
    th,
    td {
      border: 1px solid #ccc;
      padding: 5px;
      text-align: center;
    }
    th {
      background-color: #eee;
    }
  }
}

.icon-container {
    display: flex;
    justify-content: center;
    align-items: center;

}
</style>
