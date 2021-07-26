<template>
  <div>
      <div>
        <div>
          <label for="day">Day</label>
          <input type="text" v-model="day">
        </div>
        <div>
          <label for="menu">Menu</label>
          <input type="text" v-model="menu">
        </div>
        <div>
          <label for="income">Income</label>
          <input type="text" v-model="income">
        </div>
        <div>
          <label for="expenses">Expenses</label>
          <input type="text" v-model="expenses">
        </div>
        <button @click="addMenu">Add</button>
        <table>
          <thead>
            <th>#</th>
            <th>Day</th>
            <th>Menu</th>
            <th>Income</th>
            <th>Expenses</th>
          </thead>
          <tbody>
            <tr v-for="(data, index) in json" :key="index">
              <td>{{ index + 1}}</td>
              <td>{{ data.day }}</td>
              <td>{{ data.menu }}</td>
              <td>{{ data.income }}</td>
              <td>{{ data.expenses }}</td>
            </tr>
          </tbody>
        </table>
        <div>
          Total of my money is {{ total }}
        </div>
      </div>
  </div>
</template>

<script>
  import Json from 'C:/laragon/www/suwaraap/vue101-11/simple_vue/json/list.json'

export default {
  data() {
    return {
      day: '',
      menu: '',
      income: '',
      expenses: '',
      json: Json.data,
      total: 0    
    }

  },
  methods: {
    addMenu() {
      let lastForm = {
        day: this.day,
        menu: this.menu,
        income: this.income,
        expenses: this.expenses
      }
      this.json.push(lastForm)
      this.sum()
      this.clearForm()
    },
    clearForm() {
      this.day = '',
      this.menu = '',
      this.income = '',
      this.expenses = ''
    },
    sum() {
      for (let index = 0; index < json.length; index++) {
        const element = array[index];
        this.total += parseInt(this.json[index].income)
        this.total -= parseInt(this.json[index].expenses)
      }
    }
  }
  
}
</script>

<style>

</style>