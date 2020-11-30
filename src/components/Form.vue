<template>
  <form>
    <input
        type="text"
        name="unicorn-name"
        v-model="newUnicorn.name"
        placeholder="Name"
    />
    <input
        type="text"
        name="todo-description"
        v-model="newUnicorn.description"
        placeholder="Description"
    />
    <input
        type="text"
        name="todo-img"
        v-model="newUnicorn.img"
        placeholder="Url path"
    />
    <input
        type="text"
        name="todo-age"
        v-model="newUnicorn.age"
        placeholder="Unicorn age"
    />
    <span>newUnicorn: {{newUnicorn}}</span>
  </form>

</template>

<script>
export default {
  name: "Form",
  props: {
    newUnicorn: {
      type:Object
    }
  }
}
</script>

<style scoped>
input{
  display:flex;
  margin:8px;
}
</style>