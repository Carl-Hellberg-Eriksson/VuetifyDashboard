<template>
  <div>
    <h1>Dashboard!</h1>
    <v-data-table
      :headers="headers"
      :items="employees"
      :items-per-page="5"
      class="elevation-1"
      multi-sort
      @click:row="selectRow"
    ></v-data-table>
    <!-- Snackbar -->
    <v-snackbar v-model="snackbar" :timeout="timeout">
      {{ currentItem }}
      <v-btn color="pink" text @click="snackbar = false">
        Close
      </v-btn>
    </v-snackbar>
  </div>
</template>

<script>
import employeesJson from "@/data/employees.json";

export default {
  data() {
    return {
      snackbar: false,
      timeout: 2000,
      currentItem: "",
      employees: employeesJson,
      headers: [
        {
          text: "Employee ID",
          align: "start",
          sortable: false,
          value: "id",
        },
        { text: "Name", value: "name" },
        { text: "Salary", value: "salary" },
        { text: "Title", value: "title" },
      ],
    };
  },

  methods: {
    selectRow(event) {
      this.currentItem = `${event.name} -  ${event.title}`;
      this.snackbar = true;
    },
  },
};
</script>
<style></style>
