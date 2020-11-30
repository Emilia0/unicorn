<template>
  <div class="unicorn">
    <div class="unicorn__details">
      <h4> {{unicorn.name}} {{unicorn.id}}</h4>
      <h5> {{unicorn.description}}</h5>
      <span> age:{{unicorn.age}}</span>
      <button @click.prevent="$emit('remove', unicorn.id)">Remove</button>
    </div>

    <img class="unicorn__img" :src="unicorn.img"/>

  </div>

</template>

<script>
export default {
name: "Unicorn",
  props: {
   unicorn: {
     required: true,
     type: Object
   }
  }
}
</script>

<style scoped>
.unicorn{
  width:1000px;
  height:500px;
  padding:16px;
  border: solid gray 1px;
  margin:16px;
  flex-flow: row nowrap;
}
.unicorn__details{
  flex-flow:column nowrap;
}
.unicorn__img{
  width:100%;
  max-width:500px;
  height:auto;
  object-fit: contain;
}

</style>