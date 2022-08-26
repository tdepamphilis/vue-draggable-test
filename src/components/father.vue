<template>
  <div class="body">
    <draggable @change="onChange" :disabled="!AllowDraggingChildren" v-model="sorteableChildren" group="fathers" @start="drag = true" @end="drag = false" class="body">
    <child v-for="(child, index) in sorteableChildren" v-bind:key="child.id" :name="sorteableChildren[index]" @MoveIconHover="onChildMoveIconHover" />
    </draggable>
    <h4 v-if="AllowDraggingChildren">dr</h4>
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
            sorteableChildren: [],
            AllowDraggingChildren: false
        }
    },
    created(){
        this.actualizar()
        console.log('crea')
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
        },
        onChildMoveIconHover(bool){
            this.$emit('childIconHover', bool);
            
        },
        AllowDragChildToggle(bool){
            this.AllowDraggingChildren = bool;
        },
        childDrop(){
          this.$emit('childDrop');
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