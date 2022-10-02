<template>
  <v-row>
    <v-col>
      <Form />
    </v-col>
    <v-col>
      <Table />
    </v-col>
  </v-row>
</template>

<script>
import Table from '../components/Table.vue';
import Form from '../components/Form.vue';
export default { components: { Table, Form } };
</script>

<style></style>
