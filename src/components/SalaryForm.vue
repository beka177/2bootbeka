<template>
    <div>
      <form @submit.prevent="addSalary">
        <div class="form-group">
          <label for="employeeName">Ф.И.О. сотрудника</label>
          <input type="text" class="form-control" id="employeeName" v-model="employeeName" required>
        </div>
        <div class="form-group">
          <label for="salaryDate">Дата выдачи зарплаты</label>
          <input type="date" class="form-control" id="salaryDate" v-model="salaryDate" required>
        </div>
        <div class="form-group">
          <label for="workingDays">Количество отработанных дней</label>
          <input type="number" class="form-control" id="workingDays" v-model="workingDays" required>
        </div>
        <div class="form-group">
          <label for="salaryAmount">Размер заработной платы сотрудника</label>
          <input type="number" class="form-control" id="salaryAmount" v-model="salaryAmount" required>
        </div>
        <button type="submit" class="btn my-3 btn-primary">Добавить</button>
      </form>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        employeeName: '',
        salaryDate: '',
        workingDays: '',
        salaryAmount: ''
      };
    },
    methods: {
      addSalary() {
        this.$emit('add-salary', {
          name: this.employeeName,
          date: this.salaryDate,
          days: this.workingDays,
          amount: this.salaryAmount
        });
  
        this.employeeName = '';
        this.salaryDate = '';
        this.workingDays = '';
        this.salaryAmount = '';
      }
    }
  };
  </script>