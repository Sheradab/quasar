<template>
  <q-page class="bg-grey-3 column ">
    <q-list separator bordered>
      <q-item @click="task.done =!task.done"  
              :class="{'done bg-green-2' : task.done}" 
              v-for="task, index in tasks"
              :key="task.title" 
              tag="label" v-ripple>
        <q-item-section avatar>
          <q-checkbox  v-model="task.done" val="teal" color="primary" />
        </q-item-section>
        <q-item-section>
          <q-item-label>{{task.title}}</q-item-label>
        </q-item-section>
        <q-item-section v-if="task.done" side>
          <q-btn @click.stop="deleteTask(index)" push color="primary" label="Delete" />
        </q-item-section>       
      </q-item>      
    </q-list>
  </q-page>
</template>

<script>
export default {
  data() {
    return {
      tasks: [
        {
          title: "first",
          done: false
        },
        {
          title: "second",
          done: false
        },
        {
          title: "third",
          done: false
        },
        {
          title: "fourth",
          done: false
        },
        {
          title: "fifth",
          done: false
        },
        {
          title: "sixth",
          done: false
        }
      ]
    }
  },
  methods: {
    deleteTask (index){
      this.tasks.splice(index, 1);
    }
  }
}
</script>

<style lang="scss">
.done {
.q-item__label {
  text-decoration: line-through;  
  color:rgb(9, 185, 53)
  }
}
</style>