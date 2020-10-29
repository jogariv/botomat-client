<template>
    <div class="my-3 p-3 bg-white rounded shadow-sm">
        <h6 class="border-bottom border-gray pb-2 mb-0">Robots Leaderboard:</h6>
        <div v-for="robo in list" :key="robo.id" class="media text-muted pt-3">
          
          <div 
            class="media-body pb-3 mb-0 small lh-125 border-bottom border-gray"
          >
            <div
              class="d-flex justify-content-start align-items-center w-100"
            >
              <strong class="text-gray-dark col-2">{{robo.id}}</strong>
              <div class="col-8">
                  Remaining Tasks: {{robo.tasks.length}}  
                  <span v-if="robo.tasks.length == 0" class="ml-2 badge badge-secondary">Finished</span>
              </div>
              
            </div>
            
          </div>
        </div>
        
      </div>
</template>

<script>
export default {
    name: 'results',
    props: ['list']
}
</script>