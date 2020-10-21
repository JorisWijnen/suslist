<template>
  <div class="dashboard">
    <p>I'm a new vue component.</p>
    <ejs-grid :dataSource="data"> </ejs-grid>
  </div>
</template>

<script>
  export default {
    name: "DashBoard",
    data () {
    return {
      data: [
        { OrderID: 10248, CustomerID: 'VINET', EmployeeID: 5 },
        { OrderID: 10249, CustomerID: 'TOMSP', EmployeeID: 6 },
        { OrderID: 10250, CustomerID: 'HANAR', EmployeeID: 4 }]
      }
    }
  }
</script>

<style lang="css">
</style>
