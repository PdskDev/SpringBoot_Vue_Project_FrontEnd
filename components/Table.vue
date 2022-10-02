<template>
  <v-data-table :headers="headers" :items="users">
    <template v-slot:[`item.edit`]="{ item }">
      <v-btn color="success" @click="editItem(item)"> Edit</v-btn>
    </template>
    <template v-slot:[`item.delete`]="{ item }">
      <v-btn color="warning" @click="deleteItem(item)"> Edit</v-btn>
    </template>
  </v-data-table>
</template>

<script>
export default {
  data() {
    return {
      headers: [
        { text: 'Name', value: 'name' },
        { text: 'Email', value: 'email' },
        { text: 'Password', value: 'password' },
        { text: 'Edit', value: 'edit' },
        { text: 'Delete', value: 'delete' },
      ],
      users: [
        {
          name: 'NadetDev',
          email: 'email01@email.com',
          password: 'password01',
        },
        {
          name: 'ZLA',
          email: 'email02@email.com',
          password: 'password02',
        },
        {
          name: 'SYN',
          email: 'email02@email.com',
          password: 'password02',
        },
        {
          name: 'JLY',
          email: 'email03@email.com',
          password: 'password03',
        },
        {
          name: 'BSO',
          email: 'email04@email.com',
          password: 'password04',
        },
      ],
    };
  },
  computed: {
    users() {
      return this.$store.state.users.data;
    },
  },
  async fetch() {
    this.$store.commit(
      'users/storeData',
      (await this.$axios.get('http://localhost:8080/users/all')).data
    );
  },
  methods: {
    async deleteItem(id) {
      await this.$axios.delete(`http://localhost:8080/users/delete/${id}`);
      this.$store.commit(
        'users/storeData',
        (await this.$axios.get('http://localhost:8080/users/all')).data
      );
    },
    async editItem(user) {
      this.$store.commit('users/storeId', user.id);
      this.$store.commit('users/storeName', user.name);
      this.$store.commit('users/storeEmail', user.email);
      this.$store.commit('users/storePassword', user.password);
    },
  },
};
</script>

<style></style>
