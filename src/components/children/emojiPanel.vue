<template>
  <div class="all">
    <img class="emojiPic" src="../../assets/img/emoji_sprite.png">
    <div class="partsWrap">
      <emoji-parts
      v-for="(item,index) in emojis" :key="index"
      :text="item"
      class="partsClass"
      @callf="callf"
      ></emoji-parts>
    </div>
  </div>
</template>

<script>
import emojiParts from './emojiParts'
export default {
  data(){
    return{
       emojis: [
        "angry",
        "anguished",
        "astonished",
        "blush",
        "cold_sweat",
        "confounded",
        "confused",
        "cry",
        "disappointed",
        "disappointed_relieved",
        "dizzy_face",
        "expressionless",
        "fearful",
        "flushed",
        "frowning",
        "grimacing",
        "grin",
        "grinning",
        "heart_eyes",
        "hushed",
        "innocent",
        "joy",
        "kissing_closed_eyes",
        "kissing_heart",
        "laughing",
        "neutral_face",
        "no_mouth",
        "open_mouth",
        "pensive",
        "persevere",
        "relaxed",
        "relieved",
        "sleepy",
        "smile",
        "smiley",
        "smirk",
        "sob",
        "stuck_out_tongue",
        "sunglasses",
        "sweat",
        "sweat_smile",
        "scream",
        "wink",
        "unamused",
        "satisfied",
        "worried",
        "stuck_out_tongue_closed_eyes",
        "weary",
        "yum",
        "tired_face",
        "triumph",
        "stuck_out_tongue_winking_eye"
      ]
    }
  },
  name: '',
  components: {
    emojiParts
  },
  methods:{
    callf(a){
      this.$emit('callf',a)
    }
  }
}
</script>
<style lang="scss">
.all{
  font-size:0;
  .emojiPic{
    width:400px;
    height:266.67px;
    position:absolute;
    z-index:-2;
  }
  .partsWrap{
    width:400px;
    height:269.67px;
    z-index:-1;
    .partsClass{
      display:inline-block;
      width:44.45px;
      height:44.45px;
      cursor:pointer;
    }
  }
}
</style>
