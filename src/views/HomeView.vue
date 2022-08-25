<template>
  <div @mouseup="updateChildren">
    <div >
      <draggable class="container"  v-model="fathers" group="fathers" @start="drag=true" @end="drag=false">
      <father  ref="f" class="father" v-for="(father, index) in fathers" v-bind:key="father.id" :father="fathers[index]" @change="onChange"  />
      </draggable>
    </div>

  </div>
</template>

<script>
// @ is an alias to /src
import father from '../components/father.vue'
import draggable from 'vuedraggable'
export default {
  name: 'HomeView',
  components: { father, draggable  },
  data(){
    return{
      fathers: [
        {id: 1, children: [{txt: 'hola'}, {txt: 'dos'}, {txt: 'chau'}]},
        {id: 2, children: [{txt: 'Maria'}, {txt: 'juan'}]},
        {id: 3, children: [{txt: 'perro'}, {txt: 'loro'}, {txt: 'casa'}, {txt: 'auto'}]}
      ]
    }
  },
  methods:{
    updateChildren(){
        // vuelvo a asignar sorteableChildren en los padres, para que se vean los cambios 
        for (let index = 0; index < this.fathers.length; index++) {
          this.$refs.f[index].actualizar()
        }
    },
    // actualizo los hijos en el array original
    onChange(data){
      this.fathers.forEach(f => {
        if(f.id === data.id){
          f.children = data.children
        }
      });
    },
  }
}
</script>

<style scoped>
.container{
  border: solid;
  width: 100%;
  height: 100vh;
  display: flex;
  flex-direction: row;
}

.father{
  height: 45%;
  width: 25%;
  margin-left: 20px;
 margin-top: 20px;
}
</style>
