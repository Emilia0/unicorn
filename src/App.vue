<template>
  <div id="app">
    <div class="header">
      <div class="header__title">Amazing unicorns</div>
      <button id="show-modal" class="header__button" @click="showModal = true">Add new unicorn</button>
    </div>
    <div class="unicorns">
      <Unicorn
        v-for="unicorn in unicornList"
        :key="unicorn.id"
        :unicorn="unicorn"
        @remove="removeUnicorn"/>
    </div>

    <Modal v-if="showModal" @close="showModal = false">
      <template v-slot:header>
        <h3>Add a unicorn</h3>
      </template>
      <template v-slot:body>
        <Form :new-unicorn.sync="newUnicorn"/>

      </template>
      <template v-slot:footer>
        <button @click="addUnicorn">
          SUBMIT
        </button>

      </template>

    </Modal>
  </div>
</template>

<script>
import Unicorn from './components/Unicorn.vue'
import Modal from './components/Modal.vue'
import Form from './components/Form.vue'
import {UNICORNS} from './data.js';

let nextId = 5;
const createUnicorn = data => ({
  id: nextId++,
  name: data.name,
  description: data.description,
  img: data.img,
  age: data.number
})

export default {
  name: 'App',
  components: {
    Unicorn,
    Modal,
    Form
  },
  data() {
    return {
      unicornList: UNICORNS,
      showModal: false,
      newUnicorn: {}
    }
  },
  methods: {
    removeUnicorn(id) {
      this.unicornList = this.unicornList.filter((unicorn) =>
        unicorn.id !== id
      )
    },
    addUnicorn() {
      this.unicornList.push(createUnicorn(this.newUnicorn));
      this.showModal= false;
      this.newUnicorn = {}
    }
  }
}
</script>

<style>
div {
  display:flex;
}
html,
body {
  margin: 0;
  height: 100%;
  width: 100%;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  display:block;
}
.header{
  flex-flow: row nowrap;
  justify-content:space-between;
  height:50px;
  width:100%;
  background-color:deeppink;
}
.unicorns{
  flex-flow: column nowrap;
}
</style>
