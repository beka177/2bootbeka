<template>
  <div class="container mt-5">
    <SalaryForm @add-salary="addSalary"></SalaryForm>
    <SalaryList :salaries="salaries" @remove-salary="removeSalary"></SalaryList>
  </div>
</template>

<script>
import SalaryForm from './components/SalaryForm.vue';
import SalaryList from './components/SalaryList.vue';

export default {
  components: {
    SalaryForm,
    SalaryList
  },
  data() {
    return {
      salaries: []
    };
  },
  methods: {
    addSalary(salary) {
      this.salaries.push(salary);
    },
    removeSalary(index) {
      this.salaries.splice(index, 1);
    }
  }
};
</script>