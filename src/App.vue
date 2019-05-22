<template>
  <main>
    <AddCategory v-if="shouldShowAddCategory" v-on:addCategory="addCategory" />
    <div v-else>
      <AddBill v-if="shouldShowAddBill" :categories=categories v-on:addBill="addBill"/>
      <div v-else>
        <NavBar :categories=categories v-on:triggerShowAddCategory=triggerShowAddCategory />
        <div class="container flex">
          <div class="w-1/2">
      <BillsTable :bills="bills" v-on:triggerShowAddBill="triggerShowAddBill" />
          </div>
        <div class="w-1/2">
          <Chart />
        </div>
      </div>
    </div>
    </div>
  </main>
</template>

<script>
import AddCategory from "./components/AddCategory"
import AddBill from "./components/AddBill"
import BillsTable from "./components/BillsTable"
import Chart from "./components/Chart"
import NavBar from "./components/NavBar"
import Vue from 'vue'
Vue.use(require('vue-moment'))


export default {
  name: "app",
  components: {
    AddCategory,
    AddBill,
    BillsTable,
    Chart,
    NavBar
  },
  data() {
    return {
      bills: [],
      categories: [],
      shouldShowAddCategory: true,
      shouldShowAddBill: true
    }
  },
  methods: {
    addCategory(category) {
      this.categories.push(category)
      this.shouldShowAddCategory = false
    },
    addBill(bill) {
      this.bills.push(bill)
      this.shouldShowAddBill = false
    },
    triggerShowAddCategory() {
      this.shouldShowAddCategory = true
    },
    triggerShowAddBill() {
  this.shouldShowAddBill = true
    }
  },
  watch: {
    bills() {
      localStorage.setItem('bills', JSON.stringify(this.bills))
    },
    categories() {
      localStorage.setItem('categories', JSON.stringify(this.categories))
    }
  },
  mounted() {
    if (localStorage.getItem('bills')) {
    this.bills = JSON.parse(localStorage.getItem('bills'))
    }

    if (localStorage.getItem('categories')) {
      this.categories = JSON.parse(localStorage.getItem('categories'))
    }

    if (!this.categories.length && !this.categories.length) {
      this.shouldShowAddCategory = true
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
