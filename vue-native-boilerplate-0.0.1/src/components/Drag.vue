<template>
  <div>
    <div @dragover="preventDragDropSideEffect" @drop="insertCarouselSlide">
      <b-carousel
        id="carousel1"
        style="text-shadow: 1px 1px 2px #333;"
        controls
        indicators
        background="#ababab"
        :interval="4000"
        img-width="1024"
        img-height="480"
        v-model="slide"
        @sliding-start="onSlideStart"
        @sliding-end="onSlideEnd"
      >
        <!-- Text slides with image -->
        <b-carousel-slide
          v-for="(src,index) in image_sources"
          v-bind:key="index"
          v-bind:img-src="src"
          draggable="false"
        ></b-carousel-slide>
        <b-carousel-slide img-blank v-if="image_sources.length == 0"></b-carousel-slide>
      </b-carousel>
    </div>
    <div class="image-set">
      <img draggable="true" src="@/assets/1.jpg" @dragstart="prepareInsertion">
      <img draggable="true" src="@/assets/2.jpg" @dragstart="prepareInsertion">
      <img draggable="true" src="@/assets/3.jpg" @dragstart="prepareInsertion">
      <img draggable="true" src="@/assets/4.jpg" @dragstart="prepareInsertion">
    </div>
  </div>
</template>

<script>
export default {
  name: "Carousel",
  props: {},
  data() {
    return {
      slide: 0,
      image_sources: []
    };
  },
  methods: {
    onSlideStart(index) {},
    onSlideEnd(index) {},
    prepareInsertion(ev) {
      ev.dataTransfer.setData("img-src", ev.srcElement.src);
    },
    preventDragDropSideEffect(ev) {
      ev.preventDefault();
    },
    insertCarouselSlide(ev) {
      ev.preventDefault();
      this.image_sources.push(ev.dataTransfer.getData("img-src"));
      for (let i = 0; i < this.image_sources.length; i++) {
        this.image_sources[i] == "" ? this.image_sources.splice(i, 1) : void 0;
      }
      setTimeout(() => (this.slide = this.image_sources.length - 1), 0);
    }
  }
};
</script>
<style scoped>
.image-set {
  background-color: rgb(180, 178, 28);
}
.image-set > img {
  width: 25%;
  display: inline-block;
}
</style>
</script>