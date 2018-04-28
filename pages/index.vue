<template>
  <div class="flex">
      <div class="container">
        <button @click="backendCall">
            Click me!
        </button>
        <p v-if="message">
            {{message}}
        </p>
      </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
    data() {
        return {
            "message": ""
        }
    },
    methods: {
        backendCall() {
            return axios.get(process.env.helloEndpoint)
            .then(resp => {
                console.log(resp.data.input);
                return this.message = resp.data.message;
            })
        }
    }
}
</script>

<style lang="scss" scoped>
    .flex {
        height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    button {
        background-color: red;
        font-size: 28px;
    }
</style>
