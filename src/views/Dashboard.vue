<template>
  <v-container>
    <v-row>
      <v-col v-for="sale in sales" :key="sale.title" cols="12" sm="4">
        <SalesGraph :sale="sale" />
      </v-col>
    </v-row>

    <v-row>
      <v-col v-for="statistic in statistics" :key="statistic.title" cols="12" sm="6" md="3" >
        <StatisticCard :statistic="statistic"/>
      </v-col>
    </v-row>

    <v-row>
      <v-col cols="12" md="8">
        <EmployeesTable :employees="employees" @select-employ="selectEmployee"/>
      </v-col>

      <v-col>
        <EventTimeline :timeline="timeline"/>
      </v-col>
    </v-row>


    <v-snackbar
        v-model="snackbar"
        :left="$vuetify.breakpoint.mdAndUp"
    >
      You have been selected {{ text }}

      <template v-slot:action="{ attrs }">
        <v-btn
            color="pink"
            text
            v-bind="attrs"
            @click="snackbar = false"
        >
          Close
        </v-btn>
      </template>
    </v-snackbar>
  </v-container>

</template>

<script>
import employees from '../data/employees.json'
import sales from '../data/sales.json'
import statistics from '../data/statistics.json'
import timeline from '../data/timeline.json'
import EmployeesTable from "../components/EmployeesTable";
import SalesGraph from "../components/SalesGraph";
import StatisticCard from "../components/StatisticCard";
import EventTimeline from "../components/EventTimeline";
export default {
  name: "Dashboard",
  components: {EventTimeline, StatisticCard, SalesGraph, EmployeesTable},
  data () {
    return {
      employees,
      sales,
      statistics,
      timeline,
      snackbar: false,
      text: '',
    }
  },
  methods: {
    selectEmployee (employee) {
      this.snackbar = true
      this.text = `${employee.name}, ${employee.title}`
    }
  }
}
</script>

<style scoped>

</style>
