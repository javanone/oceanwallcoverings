<template>
  <div>
    <transition-group name="fade" tag="div">
      <div v-for="i in [currentIndex]" :key="i">
        <img :src="currentImg" />
      </div>
    </transition-group>
    <a class="prev" @click="prev" href="#">&#10094; Previous</a>
    <a class="next" @click="next" href="#">&#10095; Next</a>
  </div>
</template>
<script>
export default {
  name: "Slider",
  data() {
    return {
      images: [
        "https://cdn.pixabay.com/photo/2015/12/12/15/24/amsterdam-1089646_1280.jpg",
        "../../img/owc-backgrounds/hires01.jpg",
        "../../img/owc-backgrounds/hires04.jpg",
        "../../img/owc-backgrounds/hires05.jpg",
        "../../img/owc-backgrounds/hires06.jpg",
        "../../img/owc-backgrounds/hires07.jpg",
        "../../img/owc-backgrounds/hires08.jpg",
        "../../img/owc-backgrounds/hires09.jpg",
        "../../img/owc-backgrounds/hires10.jpg",
        "../../img/owc-backgrounds/hires12.jpg",
        "../../img/owc-backgrounds/hires13.jpg",
        "../../img/owc-backgrounds/hires14.jpg",
        "../../img/owc-backgrounds/hires15.jpg",
        "../../img/owc-backgrounds/hires16.jpg",
        "../../img/owc-backgrounds/hires17.jpg",
        "../../img/owc-backgrounds/hires18.jpg",
        "../../img/owc-backgrounds/hires19.jpg",
        "../../img/owc-backgrounds/hires20.jpg"
      ],
      timer: null,
      currentIndex: 0
    }
  },

  mounted: function() {
    this.startSlide();
  },

  methods: {
    startSlide: function() {
      this.timer = setInterval(this.next, 4000);
    },
    next: function() {
      this.currentIndex += 1;
    },
    prev: function() {
      this.currentIndex -= 1;
    }
  },

  computed: {
    currentImg: function() {
      return this.images[Math.abs(this.currentIndex) % this.images.length];
    }
  }
};
</script>

<style>
.fade-enter-active,
.fade-leave-active {
  transition: all 0.9s ease;
  overflow: hidden;
  visibility: visible;
  position: absolute;
  width:100%;
  opacity: 1;
}

.fade-enter,
.fade-leave-to {
  visibility: hidden;
  width:100%;
  opacity: 0;
}

img {
  height:600px;
  width:100%
}

.prev, .next {
  cursor: pointer;
  position: absolute;
  top: 40%;
  width: auto;
  padding: 16px;
  color: white;
  font-weight: bold;
  font-size: 18px;
  transition: 0.7s ease;
  border-radius: 0 4px 4px 0;
  text-decoration: none;
  user-select: none;
}

.next {
  right: 0;
}

.prev {
  left: 0;
}

.prev:hover, .next:hover {
  background-color: rgba(0,0,0,0.9);
}
</style>
