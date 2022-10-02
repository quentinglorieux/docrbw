<template>
    <img :src="imgSrc()" :alt="alt" :style="cssProps3" class="text-image" />
</template>

<script>
export default {
  props: {
    src: {
      type: String,
      required: true
    },
    alt: {
      type: String,
      required: true
    },
    size: {
      type: Number,
    },
    center: {
      type: Boolean,
    },
  },
  methods: {
    imgSrc() {
      try {
        return require(`../assets/images/${this.src}`)
      } catch (error) {
        return null
      }
    }
  },
  computed: {
    cssProps() {
      return {
        '--image-size': this.size + "%",
        '--margin': this.center,
      }
    },
    cssProps3() {
      if (this.center)
      { return  {
        '--dsiplay': 'inline', 
        '--margin': 'auto', 
        '--image-size': this.size + "%"
        }
      }
      return  { '--image-size': this.size + "%"} 
    },
  },
}
</script>

<style scoped>
.text-image {
  /* width: 100%; */
  display: inline;
  width: var(--image-size);
  margin: 5px var(--margin);
  /* border: 1px solid #fcfcfc; */
  /* border-radius: 1px; */
  /* margin: 0px auto; */
}
</style>