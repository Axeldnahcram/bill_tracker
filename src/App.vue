<template>
  <main>
    <NavBar />
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
