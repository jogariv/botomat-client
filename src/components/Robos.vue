<template>
    <div>
        <div class="d-flex align-items-center p-3 my-3 text-white-50 bg-purple rounded shadow-sm">
            
                <div class="mr-auto d-flex">
                    <div class="mr-auto">
                        <img
                        id="avatarPic"
                        class="mr-3"
                        :src="randomRobo.avatarPic"
                        alt=""
                        width="72"
                        height="72"
                        />
                    </div>
                    
                    <div class="lh-100 pt-2">
                    <h6 class="mb-0 text-white lh-100">Robot Name: <span id="roboId">{{randomRobo.id}}</span></h6>
                    <small>Type: <span id="roboType">{{randomRobo.type}}</span></small>
                    <div id="taskProcessing" class="mt-2" style="display:none">
                        <div class="spinner-border spinner-border-sm text-light" role="status">
                            <span class="sr-only">Loading...</span>
                        </div>
                        <span class="ml-2 text-white">I'm working with your request</span>
                    </div>
                    </div>
                </div>
                <div>
                    <button v-on:click="getRandomRobo()" class="btn btn-light btn-sm">Change</button>
                </div>
        </div>
        <tasks :taskList="randomRobo.tasks"></tasks>
        <results :list="roboList"></results>
    </div>

</template>

<script>

import Tasks from '@/components/Tasks.vue'
import Results from '@/components/Results.vue'


export default {
      
    name: 'robos',
    components: {
        Tasks,
        Results
    },
    props: ['roboList'],
    methods: {
        getRandomRobo() {
            this.randomRobo = this.roboList[Math.floor((Math.random() * this.roboList.length))];
        }
    },
    data() {
        return {
            randomRobo: null
            
        }
    },
    mounted(){
        this.getRandomRobo();
    }
}
</script>