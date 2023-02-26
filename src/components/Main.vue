<template>
  <div>
    <button style="margin-bottom: 15px" @click="clickBtn">
      Изменить данные
    </button>
    <Table :columns="columns" :rows="rows" :check="check" />
  </div>
</template>

<script>
import Table from "@/components/Table.vue";

export default {
  components: {
    Table,
  },
  data() {
    return {
      check: true,
      columns: [],
      rows: [],
    };
  },
  computed: {},
  methods: {
    clickBtn() {
      this.check = !this.check;
      this.columns = [];
      this.rows = [];
      this.check ? this.loadTable1() : this.loadTable2();
    },
    loadTable1() {
      this.columns = [
        "00",
        "01",
        "02",
        "03",
        "04",
        "05",
        "06",
        "07",
        "08",
        "09",
        "10",
        "11",
        "12",
        "13",
        "14",
        "15",
        "16",
        "17",
        "18",
        "19",
        "20",
        "21",
        "22",
        "23",
      ];
      this.rows = Array.from({ length: 100 }, () => ({
        data: Array.from({ length: 24 }, () => ({
          value: Math.floor(Math.random() * 999999),
        })),
      }));
    },
    loadTable2() {
      const date = new Date();
      const month = date.getMonth();
      const year = date.getFullYear();
      const daysInMonth = new Date(year, month + 1, 0).getDate();
      for (let i = 1; i <= daysInMonth; i++) {
        this.columns.push(i);
      }

      for (let i = 0; i < 10; i++) {
        this.rows.push({});
      }
    },
  },
  created() {
    this.loadTable1();
  },
};
</script>
