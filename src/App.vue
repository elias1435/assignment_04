<script setup>

import {ref, reactive} from 'vue'

const activeSlide = ref(0)

const sliderImages = [
  {
    image: 'https://images.unsplash.com/photo-1689784730988-6cafd0821f8b?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1828&q=80',
    title: 'Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Donec odio.',
  },
  {
    image: 'https://images.unsplash.com/photo-1673107287387-065fd7b9e758?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1828&q=80',
    title: 'Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Donec odio.',
  },
  {
    image: 'https://images.unsplash.com/photo-1664283382570-8cbcf4fb8387?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1828&q=80',
    title: 'Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Donec odio.',
  },
  {
    image: 'https://images.unsplash.com/photo-1628172225866-fbbec7bcbe9e?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1828&q=80',
    title: 'Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Donec odio.',
  }
]

const overlayFilter = '-webkit-filter: grayscale(100%);filter: grayscale(100%);'



</script>

<template>

<h4>Image Carousel</h4>
  <div id="carouselExampleIndicators" class="carousel slide" data-ride="carousel" data-interval="3000">
    <ol class="carousel-indicators">
      <li @click="activeSlide = index" data-target="#carouselExampleCaptions" v-for="(items, index) in sliderImages" :key="index" :class="index == activeSlide?'active':''"></li>
    </ol>
    <div class="carousel-inner">        
      <div class="carousel-item active">           
        <img height="500" :src="sliderImages[activeSlide].image" class="d-block w-100 img img-responsive" alt="...">
        <div class="carousel-caption d-none d-md-block">
          <h5>{{ sliderImages[activeSlide].title }}</h5>
          <p>{{ sliderImages[activeSlide].caption }}</p>
        </div>
      </div>  
    </div>    
    <a @click.prevent="0 == activeSlide ? activeSlide = (sliderImages.length) - 1 : activeSlide--" class="carousel-control-prev" href="#" role="button" data-slide="prev">
      <span class="carousel-control-prev-icon" aria-hidden="true"></span>
      <span class="sr-only">Previous</span>
    </a>
    <a @click.prevent="(sliderImages.length) - 1 == activeSlide ? activeSlide = 0 : activeSlide++" class="carousel-control-next" href="#" role="button" data-slide="next">
      <span class="carousel-control-next-icon" aria-hidden="true"></span>
      <span class="sr-only">Next</span>
    </a>
  </div>

</template>

<style scoped>

@media (min-width: 1093px) {

.w-100 {
    width: 800px !important;
}

}


</style>
