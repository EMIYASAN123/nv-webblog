<template>
  <div>
    <h1>Create Item</h1>
    <form v-on:submit.prevent="createUser">
      <p>id: <input type="num" v-model="user.id"></p>
      <p>password: <input type="text" v-model="user.password"></p>
      <p>name: <input type="text" v-model="user.name"></p>
      <p>brand: <input type="text" v-model="user.brand"></p>
      <p>price: <input type="num" v-model="user.price"></p>
      <p>warranty: <input type="text" v-model="user.warranty"></p>
      <p>feature: <input type="text" v-model="user.feature"></p>
      <p><button type="submit">create item</button></p>
    </form>
  </div>
</template>

<script>
import UsersService from "@/services/UsersService";

export default {
  data() {
    return {
      user: {
        id: "",
        password: "",
        name: "",
        brand: "",
        price: "",
        warranty: "",
        feature: ""
      }
    };
  },
  methods: {
    async createUser() {
      try {
        await UsersService.post(this.user)
        this.$router.push('/users')
      } catch (err) {
        console.log(err)
      }
    }
  }
};
</script>

<style></style>
