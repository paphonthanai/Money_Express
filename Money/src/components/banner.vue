<script setup>
import { ref, onMounted, onUnmounted, computed } from 'vue'

const currentSlide = ref(0)
const totalSlides = 4

let interval = null

const nextSlide = () => {
  currentSlide.value = (currentSlide.value + 1) % totalSlides
}

const prevSlide = () => {
  currentSlide.value = (currentSlide.value - 1 + totalSlides) % totalSlides
}

onMounted(() => {
  interval = setInterval(nextSlide, 5000)
})

onUnmounted(() => {
  clearInterval(interval)
})

const slideStyle = computed(() => ({
  transform: `translateX(-${currentSlide.value * 100}%)`
}))
</script>

<template>
  <div class="w-[96%] mx-auto bg-gthost flex justify-center">
    <div class="relative w-full max-w-full rounded-md overflow-hidden" style="height: 350px;">

      <!-- Slide container -->
      <div class="flex transition-transform duration-700 ease-in-out w-full" :style="slideStyle">
        <div class="flex-shrink-0 w-full">
          <img src="../assets/Image/Banner/Banner1.jfif" class="w-full h-[300px] object-cover object-top" />
        </div>
        <div class="flex-shrink-0 w-full">
          <img src="../assets/Image/Banner/Banner1.jfif" class="w-full h-[300px] object-cover object-center" />
        </div>
        <div class="flex-shrink-0 w-full">
          <img src="../assets/Image/Banner/Banner1.jfif" class="w-full h-[300px] object-cover object-bottom" />
        </div>
        <div class="flex-shrink-0 w-full">
          <img src="../assets/Image/Banner/Banner2.jpg" class="w-full h-[300px] object-cover object-bottom" />
        </div>
      </div>

      <!-- Dots -->
      <div class="mt-4">
        <div class="absolute left-1/2 transform -translate-x-1/2 flex gap-2">
          <button v-for="n in totalSlides" :key="n" @click="currentSlide = n - 1" :class="[
            'btn btn-xs px-2 border rounded-full transition-all duration-300',
            currentSlide === n - 1
              ? 'bg-yellow-400 text-black border-yellow-500'
              : 'bg-white/20 text-white border-white/30 hover:bg-white/30'
          ]">
            {{ n }}
          </button>
        </div>
      </div>
    </div>
  </div>
</template>
