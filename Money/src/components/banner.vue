<script setup>
import { ref, onMounted, onUnmounted, computed } from 'vue'

const currentSlide = ref(0)
const totalSlides = 3

let interval = null

const nextSlide = () => {
  currentSlide.value = (currentSlide.value + 1) % totalSlides
}

const prevSlide = () => {
  currentSlide.value = (currentSlide.value - 1 + totalSlides) % totalSlides
}

onMounted(() => {
  interval = setInterval(() => {
    nextSlide()
  }, 5000) // 5 วินาที
})

onUnmounted(() => {
  clearInterval(interval)
})

const slideStyle = computed(() => {
  return {
    transform: `translateX(-${currentSlide.value * 100}%)`
  }
})
</script>

<template>
  <div class="w-full bg-gthost flex justify-center">
    <div class="relative w-full rounded-md overflow-hidden" style="height: 293px; width: 1279px;">
      
      <!-- Slides container -->
      <div 
        class="flex transition-transform duration-700 ease-in-out h-full"
        :style="slideStyle"
      >
        <!-- Slide 1 -->
        <div class="flex-shrink-0 w-full h-full">
          <img src="@/assets/Image/Banner/Banner1.jfif" class="w-full h-full object-cover object-top" alt="banner1" />
        </div>
        <!-- Slide 2 -->
        <div class="flex-shrink-0 w-full h-full">
          <img src="@/assets/Image/Banner/Banner1.jfif" class="w-full h-full object-cover object-center" alt="banner2" />
        </div>
        <!-- Slide 3 -->
        <div class="flex-shrink-0 w-full h-full">
          <img src="@/assets/Image/Banner/Banner1.jfif" class="w-full h-full object-cover object-bottom" alt="banner3" />
        </div>
      </div>

      <!-- ปุ่มซ้ายขวา -->
      <div class="absolute flex justify-between transform -translate-y-1/2 left-2 right-2 top-1/2">
        <button @click="prevSlide" class="btn btn-circle btn-sm md:btn-md">❮</button>
        <button @click="nextSlide" class="btn btn-circle btn-sm md:btn-md">❯</button>
      </div>

    </div>
  </div>
</template>
