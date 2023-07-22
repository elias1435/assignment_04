<script setup>

import {ref, reactive} from 'vue'

const activeSlide = ref(0)

const sliderImages = [
  {
    image: 'https://images.unsplash.com/photo-1682687982046-e5e46906bc6e?ixlib=rb-4.0.3&ixid=M3wxMjA3fDF8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80',
    title: 'First Slide Label',
  },
  {
    image: 'https://images.unsplash.com/photo-1682687982167-d7fb3ed8541d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDF8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=871&q=80',
    title: 'Second Slide Label',
  },
  {
    image: 'https://images.unsplash.com/photo-1682687980918-3c2149a8f110?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDl8fHxlbnwwfHx8fHw%3D&auto=format&fit=crop&w=500&q=60',
    title: 'Third Slide Label',
  },
  {
    image: 'https://images.unsplash.com/photo-1682687982185-531d09ec56fc?ixlib=rb-4.0.3&ixid=M3wxMjA3fDF8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=870&q=80',
    title: 'Fourth Slide Label',
  },
  {
    image: 'https://images.unsplash.com/photo-1682695797873-aa4cb6edd613?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDN8fHxlbnwwfHx8fHw%3D&auto=format&fit=crop&w=500&q=60',
    title: 'Fifth Slide Label',
  }
]

const overlayFilter = '-webkit-filter: grayscale(100%);filter: grayscale(100%);'

</script>

<template>

<h4>Image Carousel</h4>
  <div id="carouselExampleCaptions" class="carousel" data-ride="carousel">    
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
  <ol class="carousel-thumnails">
    <img @click="activeSlide = index" height="20" :style="activeSlide != index?overlayFilter:''" style="cursor: pointer;" class="mx-1" v-for="(thumnail, index) in sliderImages" :key="index" :src="thumnail.image" alt="">
  </ol>

</template>

<style scoped>


</style>
