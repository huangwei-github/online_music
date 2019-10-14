<template>
  <div id="app">
    <div class="search-box">
      <input class="form-control" type="text"  placeholder="搜索音乐，歌手，歌词，mv" v-model="keywords">
      <button class="btn btn-primary" @click="search">SOU一下</button>
    </div><br>
    <button class="btn btn-default" data-toggle="modal" data-target="#myModal">
            <span class="glyphicon glyphicon-camera"></span>定制皮肤
    </button>

    <!-- Modal -->
    <div class="modal fade" id="myModal" tabindex="-1" role="dialog" aria-labelledby="myModalLabel">
      <div class="modal-dialog" role="document">
        <div class="modal-content">
          <div class="modal-header">
            <button type="button" class="close" data-dismiss="modal" aria-label="Close"><span aria-hidden="true">&times;</span></button>
            <h4 class="modal-title" id="myModalLabel">定制个性皮肤</h4>
          </div>
          <div class="modal-body">
            <input type="text" name="" id="" placeholder="请在此处粘贴您的背景图片地址" class="form-control" v-model="imglink">
          </div>
          <div class="modal-footer">
            <button type="button" class="btn btn-danger" data-dismiss="modal">关闭</button>
            <button type="button" class="btn btn-primary" @click="changeImage">保存</button>
          </div>
        </div>
      </div>
    </div>

    <Content :musics='musics' @playStatus="getPlayStatus"></Content>
    <Control :playStatus="playStatus"></Control>
    
  </div>
</template>

<script>
import Content from './components/Content.vue'
import Control from './components/Control.vue'

export default {
    data() {
       return {
         keywords: '',
         musics: {},
         imglink: '',
         playStatus: {}
     }
    },
    components:{
      Content,
      Control
    },
    created: function(){
        this.$http.get('https://api.mlwei.com/music/api/?key=523077333&id=热门&type=so&cache=0&size=hq&nu=10')
        .then( (res)=>{
          this.musics = res.body.Body;
        })
    },
    methods:{
      search: function(){
        this.$http.get('https://api.mlwei.com/music/api/?key=523077333&id='+ this.keywords +'&type=so&cache=0&size=hq&nu=10')
        .then( (res)=>{
          this.musics = res.body.Body;
        })
      },
      changeImage: function(){
          $('#app').css({'background-image':'url('+this.imglink+')'});
      },
      getPlayStatus: function(playStatus){
          this.playStatus = playStatus;  
      }

      
    }
}

</script>

<style scoped>
#app{
  height: 100%;
  width: 100%;
}
.search-box{
  margin-left: 35%;
  margin-top: 4%;
}
.search-box input{
  display: inline;
  width: 30%;
}
button[class='btn btn-default']{
  float: right;
  margin-right: 160px;
  margin-top: 5px;
}


</style>
