<template>
  <form @submit.prevent="onSubmit">
    <input type="text" v-model="title">
    <button type="submit">Create</button>
  </form>
</template>

<script>
  export default {
    data () {
      return {
        title: ''
      }
    },

    methods: {
      onSubmit () {
        if (this.title.trim()) {
          const newTodo = {
            id: Date.now(),
            title: this.title,
            completed:false
          }
          this.$emit('add-todo', newTodo)
          this.title = ''
        }
      }
    }
  }
</script>

<style scoped>
  form {
    display: flex;
    justify-content: space-between;
    margin-bottom: .5rem;
  }

  input {
    flex: 0 0 90%;
    padding: 0;
    box-sizing: border-box;
  }

  input:focus {
    outline: none;
  }

  button {
    font-size: 20px;
    color: #fff;
    text-transform: uppercase;
    flex: 0 0 10%;
    background: #22b325;
    border: none;
  }

  button:active, button:focus {
    outline: none;
  }
</style>
