<script>
  export default {
    data() {
      return {
        count: 0,

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
      }

    },
  }
</script>

<template>
  <div>
    <h1>Hello World</h1>
    <p><button @click="increment()">+</button>{{ count }}<button @click="decrement()">-</button></p>
    <br>
    <pre>
      {{ object }}
    </pre>
    <button @click="modifyObect()">Modify Object</button>
    <br>
    <p>{{ inputText }}</p>
    <input type="text" v-model="inputText">
    <button @click="addData">Add Data</button>
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
