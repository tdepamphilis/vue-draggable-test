<template>
  <div class="container">
    <v-icon class="button" @mouseenter="onMoveIconMouseEnter" @mouseleave="onMoveIconMouseLeave"  >mdi-arrow-expand</v-icon>
    <h2 class="name">{{name.txt}}</h2>
  </div>
</template>

<script>

export default {
    name: 'childComponent',
    props: ['name'],
    methods:{
        onMoveIconMouseEnter(){
            this.$emit('MoveIconHover', true);
        },
        onMoveIconMouseLeave(){
            //this.$emit('MoveIconHover', false);
        }
    }
}
</script>

<style>
.container{
    border: solid 1px grey;
    margin-top: 5px;
    margin-left: 5px;
    margin-right: 5px;
    display: flex;
    justify-content: center;
}
.button{
    margin-right: auto;
    margin-left: 15px;
}
.button:hover{
    cursor: grab;
}
.name{
    margin-right: auto;
}
</style>