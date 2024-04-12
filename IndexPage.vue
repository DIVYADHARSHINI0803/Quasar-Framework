<template>
  <q-page padding>
    <q-btn label="Add User" @click="showAddUserModal = true" />
    <q-table
      title="Users List"
      :rows="users"
      :columns="columns"
      row-key="email"
    />
    <q-dialog v-model="showAddUserModal">
      <q-card>
        <q-card-section>
          <div class="text-h6">Add User</div>
        </q-card-section>
        <q-card-section>
          <q-form @submit="addUser">
            <q-input v-model="newUser.username" label="Username" />
            <q-input v-model="newUser.email" label="Email" />
            <q-input v-model="newUser.first_name" label="First Name" />
            <q-input v-model="newUser.last_name" label="Last Name" />
            <q-btn label="Add" type="submit" color="primary" />
          </q-form>
        </q-card-section>
      </q-card>
    </q-dialog>
  </q-page>
</template>

<script>
export default {
  data () {
    return {
      showAddUserModal: false,
      users: [],
      newUser: {
        username: '',
        email: '',
        first_name: '',
        last_name: ''
      },
      columns: [
        { name: 'username', required: true, label: 'Username', align: 'left', field: row => row.username, sortable: true },
        { name: 'email', align: 'left', label: 'Email', field: 'email', sortable: true },
        { name: 'first_name', label: 'First Name', field: 'first_name', sortable: true },
        { name: 'last_name', label: 'Last Name', field: 'last_name', sortable: true }
      ]
    }
  },
  methods: {
    addUser () {
      this.users.push(this.newUser)
      this.newUser = { username: '', email: '', first_name: '', last_name: '' }
      this.showAddUserModal = false
    }
  }
}
</script>
