<script>
  import api from './api';

  export default {
    data() {
      return {
        count: 0,
        users: [],
        object: {
          nested: { count: 0 },
          array: ['foo', 'bar']
        },

        inputText: ''
      }
    },
    methods: {
      increment() {
        this.count++;
      },

      decrement() {
        this.count--;
      },

      modifyObect() {
        this.object.nested.count++
        this.object.array.push('bazz')
      },

      addData() {
        this.object.array.push(this.inputText)
        this.inputText = ''
      },

      async fetchUsers() {
         const response = await api.get('/users')
         this.users = response.data
      }

    },

    async mounted() {
      await this.fetchUsers()
    },
  }
</script>

<template>
  <div>
    <h1>Hello World</h1>
    <!-- <p><button @click="increment()">+</button>{{ count }}<button @click="decrement()">-</button></p>
    <br>
    <pre>
      {{ object }}
    </pre>
    <button @click="modifyObect()">Modify Object</button>
    <br>
    <p>{{ inputText }}</p>
    <input type="text" v-model="inputText">
    <button @click="addData">Add Data</button>
    <pre>{{ users }}</pre> -->
    <table>
      <thead>
        <tr>
          <th>ID</th>
          <th>Username</th>
          <th>Name</th>
          <th>Email</th>
          <th>Phone</th>
          <th>Company</th>
          <th>Website</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(u, index) in users" :key="u.id">
          <td>{{ u.id }}</td>
          <td>{{ u.username }}</td>
          <td>{{ u.name }}</td>
          <td>{{ u.email }}</td>
          <td>{{ u.phone }}</td>
          <td>{{ u.company.name }}</td>
          <td>{{ u.website }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
