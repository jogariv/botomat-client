<template>
    <div class="my-3 p-3 bg-white rounded shadow-sm">
        <h6 class="border-bottom border-gray pb-2 mb-0">Tasks</h6>

        <div v-if="taskList.length == 0" class="alert mt-2" role="alert">
          No more tasks...
        </div>

        <div :id="task.id" v-for="(task, index) in taskList" :key="task.id" class="media text-muted pt-3 border-bottom border-gray">
          <p 
            class="media-body pb-3 mb-0 small lh-125"
          >
          <label :for="task.id"><strong>{{task.id}}</strong>: {{task.description}}</label>
          <br/>
          <label>ETA: {{task.eta}}ms</label>
          
          </p>

        <div>
          <button v-on:click="completeTask(index, task.eta)" class="btn btn-light btn-sm">
            <span :id="task.id" v-if="processing" class="spinner-grow spinner-grow-sm" role="status" aria-hidden="true"></span>
            Complete Task
          </button>
        </div>

        </div>

        <small class="d-block text-right mt-3">
          <span>Total of tasks: <strong>{{taskList.length}}</strong></span>
        </small>
    </div>
</template>

<script>
export default {
    name: 'tasks',
    props: ['taskList'],
    data(){
      return {
        processing: false
      }
    },
    methods: {
      processingTask: function(i){
          console.log(i);
          this.taskList.splice(i, 1);
          document.getElementById('taskProcessing').style.display = 'none';
      },
      completeTask: function(idx, eta ){
          document.getElementById('taskProcessing').style.display = 'block';
          setTimeout( () => this.processingTask(idx), eta);
      }
    }
}
</script>