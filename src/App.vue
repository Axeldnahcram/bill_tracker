<template>
  <main>
    <AddCategory v-if="shouldShowAddCategory" v-on:addCategory="addCategory" />
    <NavBar :categories=categories v-on:triggerShowAddCategory=triggerShowAddCategory />
    <div class="container flex">
      <div class="w-1/2">
        <BillsTable />
      </div>
      <div class="w-1/2">
        <Chart :bills="activeBills" />
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
      shouldShowAddCategory: true
    }
  },
  methods: {
    addCategory(category) {
      this.categories.push(category)
      this.shouldShowAddCategory = false
    },
    triggerShowAddCategory() {
      this.shouldShowAddCategory = true
    }
  },
  watch: {
    categories() {
      localStorage.setItem('categories', JSON.stringify(this.categories))
    }
  },
  mounted() {
    if (localStorage.getItem('categories')) {
      this.categories = JSON.parse(localStorage.getItem('categories'))
    }

    if (!this.categories.length) {
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
