<template>
    <div>
      <table class="table">
        <thead>
          <tr>
            <th>#</th>
            <th>Ф.И.О. сотрудника</th>
            <th>Дата выдачи зарплаты</th>
            <th>Количество отработанных дней</th>
            <th>Сумма заработной платы (без налогов)</th>
            <th>Сумма заработной платы (с налогами)</th>
            <th>Действие</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(salary, index) in salaries" :key="index">
            <td>{{ index + 1 }}</td>
            <td>{{ salary.name }}</td>
            <td>{{ salary.date }}</td>
            <td>{{ salary.days }}</td>
            <td>{{ salary.amount }}</td>
            <td>{{ (salary.amount * 0.85).toFixed(2) }}</td>
            <td><button @click="removeSalary(index)" class="btn btn-danger">Удалить</button></td>
          </tr>
        </tbody>
      </table>
      <div class="mt-3">
        <h5>Общая сумма (без налогов): {{ totalAmount }}</h5>
        <h5>Общая сумма (с налогами): {{ totalAmountAfterTax }}</h5>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: ['salaries'],
    methods: {
      removeSalary(index) {
        this.$emit('remove-salary', index);
      }
    },
    computed: {
      totalAmount() {
        return this.salaries.reduce((sum, salary) => sum + salary.amount, 0).toFixed(2);
      },
      totalAmountAfterTax() {
        return this.salaries.reduce((sum, salary) => sum + (salary.amount * 0.85), 0).toFixed(2);
      }
    }
  };
  </script>