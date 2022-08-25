<template>
  <div class="container">
    <h2>{{name.txt}}</h2>
  </div>
</template>

<script>

export default {
    name: 'childComponent',
 
    props: ['name']
}
</script>

<style>
.container{
    border: solid 1px grey;
    margin-top: 5px;
    margin-left: 5px;
    margin-right: 5px;
}
</style>