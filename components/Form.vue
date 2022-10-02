<template>
  <v-form>
    <h2>User Information</h2>
    <v-text-field v-model="id" label="Id"></v-text-field>
    <v-text-field v-model="name" label="Name"></v-text-field>
    <v-text-field v-model="email" label="Email"></v-text-field>
    <v-text-field v-model="password" label="Password"></v-text-field>
    <v-button @click="submit({ id, name, email, password })">{{
      id ? 'Edit' : 'Submit'
    }}</v-button>
  </v-form>
</template>

<script>
export default {
  data: {
    id: {
      get() {
        return this.$store.state.user.id;
      },
      set() {
        this.$store.commit('user/storeId', id);
      },
    },
  },
};
</script>

<style></style>
