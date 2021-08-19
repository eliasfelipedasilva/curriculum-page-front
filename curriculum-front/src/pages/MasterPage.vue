<template>
  <v-container class="mt-12">
    <v-data-table :headers="headers" :items="items" :loading="loading" />
  </v-container>
</template>

<script>

import { getTableData } from "../api";

export default {
  name: "MasterPage",
  created() {
    this.loadItems();
  },
  data() {
    return {
      loading: false,
      items: [],
      headers: [
        {
          text: "name",
          value: "name",
          sortable: false
        },
        {
          text: "lastName",
          value: "lastName",
          sortable: false
        },
        {
          text: "dateOfBirth",
          value: "dateOfBirth",
          sortable: false
        }
      ]
    };
  },
  methods: {
    async loadItems() {
      try {
          this.loading = true;
          this.items = await getTableData();
      } finally {
          this.loading = false;
      }
      
    }
  }
};
</script>
