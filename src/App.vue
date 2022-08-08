<template>
<h1>Hello app</h1>
  <h1>{{ title }}</h1>
  <p>Welcome...</p>
  <teleport to='.modals' v-if="showModal">
    <ModalUser theme = 'sale' @close='toggleModal'><!-- sử dụng Emitting custom events --> 
    <template v-slot:links>
      <a href="#">sign up now</a>
      <a href="#">more info</a>
    </template>
    <h1>Ninja Giveaway</h1>
    <p>Grab you ninja swag for half price!</p>
    </ModalUser>
  </teleport>

<teleport to='.modals' v-if="showModalTwo">
    <ModalUser @close='toggleModalTwo'><!-- sử dụng Emitting custom events --> 
    <h1>Sign up to the newsletter</h1>
    <p>For updates and promo codes</p>
    </ModalUser>
</teleport>

  <button @click.alt="toggleModal">Open Modal(alt)</button>
  <button @click="toggleModalTwo">Open Modal Two</button>
  <p></p>
  <button @click="count++">add 1</button>
  <p>Count is: {{count}}</p>
  <UserList msg ="Chuyển data từ cha sang con!"/>
  
</template> 

<script>
import ModalUser from "./components/ModalUser.vue";
import UserList from "./components/UserList.vue"

export default {
  name: "App",
  components: { ModalUser , UserList },
  data() {
    return {
      title: 'My First Vue App :))',
      count : 0,
      showModal: false, // sử dụng Emitting custom events
      showModalTwo: false,
    };
  },
 methods: {
  toggleModal(){
    this.showModal = !this.showModal // sử dụng Emitting custom events
  },
  toggleModalTwo(){
    this.showModalTwo = !this.showModalTwo // sử dụng Emitting custom events
  },
 }
};
</script>

<style>
#app, .models{
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1{
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
