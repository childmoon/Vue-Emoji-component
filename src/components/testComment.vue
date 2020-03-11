<template>
 <div class="contentwrap">
    <div class="contentheader">
      <div class="row"
      v-for="(item,index) in mesObj.mesArr" 
      :key="index"
      >
        <div>
          <img class="headerimg" src="../assets/img/heading.jpg">
          <span class="headername">zzzzzzzaniu</span>
        </div>
        <div v-html="item"></div>
      </div>
    </div>

    <textarea class="contentarea" v-model="areaText"></textarea>
    
    <div class="contentfooter">
      <div class="footerwrap">
        <img class="emojibtn" src="../assets/img/face_logo.png" @click="showePanel">
        <a class="emojia"><button class="submitMes" @click="submitMess">发表评论</button></a>
      </div>
      <div v-if="togglePanel">
        <emoji-panel @callf="receive"></emoji-panel>
      </div>
    </div>

 </div>
</template>

<script>
import emojiPanel from './children/emojiPanel'
export default {
  name: 'app',
  components: {
    emojiPanel
  },
  data(){
    return{
      togglePanel:false,
      areaText:'',
      mesObj:{
        mesArr:[]
      }
    }
  },
  methods:{
    showePanel(){
      this.togglePanel=!this.togglePanel
    },
    receive(a){
      var par=''
      par+='['+a+']'
      this.areaText+=par
    },
    submitMess(){   
      let um=this.areaText.replace(/\[.*?\]/g,function(word){
        let proword=word.substr(1,word.length-2)
        return `<span class="emoji-${proword} emoji-initbackground"></span>`
      })
      console.log(this.mesObj)
      this.mesObj.mesArr.push(um)
      this.areaText=''
      this.togglePanel=false
    }
  }
}
</script>
<style lang="scss">

.contentwrap{
  .contentheader{
    .row{
      margin-bottom:22px;
      .headerimg{
        width:50px;
        height:50px;
        border-radius:50%;
        margin-right:15px;
        margin-bottom:10px;
      }
      .headername{
        display:inline-block;
        position:relative;
        bottom:28px;
        font-size:20px
      }
    }
    .emoji-initbackground{
      display:inline-block;
      zoom:0.4;
      background-image:url('../assets/img/emoji_sprite.png')
    }
  }
  .contentarea{
    overflow:hidden;
    width:400px;
    height:100px;
  }
  .contentfooter{
    .footerwrap{
      height:46px;
      .emojibtn{
        width:40px;
        height:40px;
        cursor:pointer;  
        &:hover{
          opacity:0.85;
        }
      }
      .emojia{
        float:right;
        height:30px;
        line-height:46px;
        .submitMes{
          width:90px;
          height:35px;
          background-color:#1296db;
          color:#ffffff;
          border:none;
          border-radius: 20px;
          cursor:pointer;
          outline:none;
          box-shadow:0 3px 3px 0px rgba(0, 0, 0, 0.4);  
          &:hover{
           opacity:0.85;
          }
        }
      }
    }
  }
}

@import "../assets/css/emoji.css"; // 导入精灵图样式
</style>