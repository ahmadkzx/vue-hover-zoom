<template>
  <div
    @mousemove="zoom($event)"
    :style="`background-image: url('${imageUrl}'); background-size: ${zoomPercent}%;`"
    :class="['hover-zoom-image', animation, { 'zoom-cursor': zoomCursor }, { 'show': isActive || !showWhenImageLoaded }]"
  >
    <img :src="imageUrl" :alt="imageAlt" loading="lazy">
  </div>
</template>

<script>
export default {
  name: 'HoverZoom',

  props: {
    imageUrl: {
      required: true,
      type: String,
      default: 'https://statics.basalam.com/public/users/DDJq/2101/M7C7WqBSrvJ0hPtxP50k3awUXMlfltezSD6oldSJ.jpeg_512X512X70.jpeg'
    },
    imageAlt: {
      required: false,
      type: String
    },
    zoomPercent: {
      default: 200,
      type: Number
    },
    zoomCursor: {
      default: true,
      type: Boolean
    },
    animation: {
      default: 'fade',
      type: String
    },
    showWhenImageLoaded: {
      default: false
    }
  },

  data: () => ({
    isActive: false
  }),

  mounted() {
    if (this.showWhenImageLoaded) this.$el.children[0].addEventListener("load", () => {
      this.isActive = true
    });
  },

  methods: {
    zoom(event){
      let zoomer = event.currentTarget;
      let offsetX = 0;
      let offsetY = 0;
      offsetX = (event.offsetX) ? event.offsetX : event.touches[0].pageX;
      offsetY = (event.offsetY) ? event.offsetY : event.touches[0].pageY;
      let x = offsetX / zoomer.offsetWidth*100;
      let y = offsetY / zoomer.offsetHeight*100;
      this.$el.style.backgroundPosition = `${x}% ${y}%`;
    }
  }
}
</script>

<style scoped>
.hover-zoom-image {
  position: relative;
  overflow: hidden;
  opacity: 0;
  width: 400px;
}

.hover-zoom-image.show {
  opacity: 1;
}

.hover-zoom-image.zoom-cursor {
  cursor: zoom-in;
}

.hover-zoom-image img {
  width: 100%;
  margin-bottom: -4px;
  transition: all .3s linear;
}

.hover-zoom-image.fade:hover img {
  opacity: 0;
}

.hover-zoom-image.shrink:not(.growup):hover img {
  transform: scale(0);
}

.hover-zoom-image.growup:not(.shrink):hover img {
  transform: scale(1.5);
}

.hover-zoom-image.slideup:not(.slidedown):hover img {
  transform: translateY(-100%);
}

.hover-zoom-image.slidedown:not(.slideup):hover img {
  transform: translateY(100%);
}
</style>