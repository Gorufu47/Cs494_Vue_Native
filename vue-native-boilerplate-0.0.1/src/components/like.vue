<template>
 
       <view >
          <touchable-opacity 
            :on-press="clike"
            :style="{backgroundColor:'#4db8ff'}">
              <text>LIKE</text>
          </touchable-opacity>
          <text>{{like}}</text>

          <touchable-opacity 
            :on-press="clove"
            :style="{backgroundColor:'#ff66b3'}">
              <text>LOVE</text>
          </touchable-opacity>
          <text>{{love}}</text>

          <touchable-opacity 
            :on-press="chaha"
            :style="{backgroundColor:'#ffff66'}">
              <text>HAHA</text>
          </touchable-opacity>
          <text>{{haha}}</text>

          <touchable-opacity 
            :on-press="cwow"
            :style="{backgroundColor:'#99ff66'}">
              <text>WOW</text>
          </touchable-opacity>
          <text>{{wow}}</text>

          <touchable-opacity 
            :on-press="csad"
            :style="{backgroundColor:'#a3c2c2'}">
              <text>SAD</text>
          </touchable-opacity>
          <text>{{sad}}</text>

          <touchable-opacity 
            :on-press="cangry"
            :style="{backgroundColor:'#ff6600'}">
              <text>ANGRY</text>
          </touchable-opacity>
          <text>{{angry}}</text>

          <button
        :on-press="onPressLearnMore"
        title="Reset"
        color="#000000"
    />

       </view>
</template>

<script>
export default {
 props: {
            like: String,
            love: String,
            haha: String,
            wow: String,
            sad: String,
            angry: String
        },
        methods: {
            clike: function () {
                this.like++;
            },
            clove: function () {
                this.love++;
            },
            chaha: function () {
                this.haha++;
            },
            cwow: function () {
                this.wow++;
            },
            csad: function () {
                this.sad++;
            },
            cangry: function () {
                this.angry++;
            },
            onPressLearnMore: function() {
            this.like=0;
            this.love=0;
            this.haha=0;
            this.wow=0;
            this.sad=0;
            this.angry=0;
            }
        }
}
</script>

<style>

</style>