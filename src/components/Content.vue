<template>
    <div id="content">
        <ul class="nav nav-tabs bg-info" role="tablist">
            <li role="presentation"><a href="#">音乐</a></li>
            <li role="presentation"><a href="#">歌手</a></li>
            <li role="presentation"><a href="#">歌词</a></li>
            <li role="presentation"><a href="#">MV</a></li>
        </ul>
        <hr>
        <table>
            <thead>
                <td>操作</td>
                <td>歌曲名称</td>
                <td>歌手</td>
                <td>专辑</td>
            </thead>
            <tr v-for="(music,index) in musics" :key="music.mid">
                <td><a @click="play(index)"><span class="glyphicon glyphicon-play-circle"></span></a></td>
                <td>{{ music.title }}</td>
                <td>{{ music.author }}</td>
                <td>{{ music.album }}</td>
                <audio controls id="audio">
                    <source :src="music.url" type="audio/mpeg">
                </audio>
            </tr>
        </table>
    </div>
</template>

<script>
export default {
    props:['musics'],
    data(){
        return{
            playStatus : {'isPlay':false,'currentTime':0}
        }
    },
    methods:{
        play: function(index){  
                var audio = document.getElementsByTagName('audio')[index]; 
                if(audio.paused){
                    audio.load();
                    audio.play();
                    this.playStatus.isPlay = true;
                    this.playStatus.currentTime = audio.currentTime;
                    this.$emit('playStatus',this.playStatus);
                }else{
                    audio.pause();
                    this.playStatus.isPlay = false;
                    this.$emit('playStatus',this.playStatus);
                }   
            
            
       }
    }
    
}
</script>

<style scoped>
    ul{
        width: 80%;
        margin-left: 10%;
    }
    table{
        width: 80%;
        margin-left: 10%;
        line-height: 30px;
    }
    table>tr>td{
        border-bottom: 1px solid rgb(79.8%, 96%, 79.8%);
    }
    button{
        margin: 0;
        padding: 0;
        border: 1px solid transparent;  
        outline: none;  
        background-color:rgb(100%, 100%, 100%);
    }
    audio{
        display: none;
    }

</style>


