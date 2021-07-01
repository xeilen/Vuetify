<template>
  <v-data-table
      :headers="headers"
      :items="employees"
      :items-per-page="5"
      class="elevation-1"
      multi-sort
      @click:row="selectRow"
  />
</template>

<script>
export default {
  name: "EmployeesTable",
  props: {
    employees: {
      type: Array,
      required: true
    }
  },
  data () {
    return {
      headers: [
        {
          text: 'Name',
          align: 'start',
          sortable: false,
          value: 'name',
        },
        { text: 'Position', value: 'title' },
        { text: 'ID', value: 'id' },
        { text: 'Salary', value: 'salary' },
      ],
    }
  },
  methods: {
    selectRow (e) {
      const employee = {
        name: e.name,
        title: e.title
      }

      this.$emit('select-employ', employee)
    }
  }

}
</script>

<style scoped>

</style>
