<template>
  <div class="body">
    <draggable  @change="onChange"  v-model="sorteableChildren" group="people" @start="drag=true" @end="drag=false" class="body">
    <child v-for="(child, index) in sorteableChildren" v-bind:key="child.id" :name="sorteableChildren[index]"  />
    </draggable>
  </div>
</template>

<script>
import draggable from 'vuedraggable'
import child from '../components/child.vue'
export default {
  components: { child, draggable },
    name: 'FatherComponent',
    props: ['father'],
    data(){
        return{
            sorteableChildren: []
        }
    },
    created(){
        this.actualizar()
    },
    methods:{
        actualizar(){
           this.sorteableChildren = this.father.children
        },
        onChange(){
            

            let data = {
                children: this.sorteableChildren,
                id: this.father.id
            }
            console.log(this.sorteableChildren)
            this.$emit('change', data)
        }
    }
}
</script>

<style>
.body{
    border: solid 3px;
    height: 100%;
    width: 100%;
}
</style>