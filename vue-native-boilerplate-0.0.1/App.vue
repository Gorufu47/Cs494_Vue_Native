<template>
<scroll-view :content-container-style="{contentContainer: {
        paddingVertical: 20
    }
    }">
    <view class="container">
      <game/>

  <like like="0" wow="0" sad="0" love="0" haha="0" angry="0"></like>
  <facul>
    </view>
</scroll-view>
  
  
</template>

<script>
import React from "react";

import Game from "./src/components/game.vue";
import Like from "./src/components/like.vue";
import Facul from "./src/components/facul.vue";




export default {
  components: { Game , Like , Facul}
};
</script>

<style>
.container {
  background-color: #FFFFFF;
  flex: 1;
  padding-top: 40px;
  align-items: center;
}
.main {
  flex: 1;
  max-width: 400px;
  align-items: center;
}
</style>
