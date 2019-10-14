<template>
    <div id="control">
        <button class="btn btn-primary">
            <span class="glyphicon glyphicon-fast-backward"></span>
        </button>
        <button class="btn btn-primary" @click="play">
            <span :class="playStatus.isPlay ? 'glyphicon glyphicon-pause' : 'glyphicon glyphicon-play'"></span>
        </button>
        <button class="btn btn-primary">
            <span class="glyphicon glyphicon-fast-forward"></span>
        </button>
        <div class="progress" >
            <div class="progress-bar" role="progressbar" aria-valuenow="60" aria-valuemin="0" aria-valuemax="100">
                <span class="sr-only">60% Complete</span>
            </div>
        </div>
        <div id="other">
            <button>词</button>
            <button>
                <span class="glyphicon glyphicon-repeat"></span>
            </button>
             <button>
                <span class="glyphicon glyphicon-film"></span>
            </button>
            <button>
                本
            </button>
        </div>

    </div>


</template>


<script>
export default {
    props: ['playStatus'],
    data(){
        return{
            playcss: 'glyphicon glyphicon-play', 
        }
    },
    methods:{
        play:function(){
            
            
        }
    }

    
}
</script>

<style scoped>
    #control{
        width: 80%;
        padding-left: 10%;
        padding-top: 3%;
    }
    button{
        height: 40px;
        width: 40px;  
        border-radius: 50%;
        margin-right: 20px;
    }
    #progress{
        width: 60%;
        height: 3px;
    }
    div[class='progress']{
        height: 3px;
        width: 30%;
        position: absolute;
        left: 24%;
        top: 87%;
    }
    div[class='progress-bar']{
        width: 60%;
        height: 3px;
    }
    #other{
        position: absolute;
        left: 75%;
        top: 84%;

    }
    

</style>

