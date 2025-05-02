<script setup>
import { ref, onMounted } from 'vue'
import { RouterLink, useRouter } from 'vue-router'

import iconTheme from '@/components/icons/iconTheme.vue'

const isLoggedIn = ref(false)

const router = useRouter()
const searchText = ref('')

onMounted(() => {
  if (localStorage.getItem('login')) {
    isLoggedIn.value = true
  }
})

const login = () => {
  isLoggedIn.value = true
  localStorage.setItem('login', true)
  window.location.reload()
}

const logout = () => {
  isLoggedIn.value = false
  localStorage.removeItem('login')
  localStorage.removeItem('cart-item')
  localStorage.removeItem('checkout-data')
  window.location.reload()
}

const handleEnter = (event) => {
  if (event.key === 'Enter') {
    router.push({
      name: 'search',
      query: {
        q: searchText.value
      }
    })
  }
}
</script>

<template>
  <div class="">
    <div class="grid grid-cols-1 
      sm:grid-cols-2 items-center h-24 py-1 space-between 
      bg-gradient-to-r from-[#350534] via-[#940691] to-[#350534]">
      <div class="text-[#fff]">
        <div class="hidden sm:flex flex-1">
          <RouterLink to="/" class="
            ml-4
            border-none
            btn btn-ghost
            normal-case
            text-[3em]
            text-[#fff]
            font-bold
            transition-transform
            duration-300
            hover:scale-105
            hover:bg-transparent
            hover:text-white
            hover:shadow-none
            hover:border-none" style="
            -webkit-text-stroke: 0.5px #90D5FF; /* ขอบตัวหนังสือสีน้ำเงิน */
            text-shadow: 
              0 0 5px #90D5FF,
              0 0 10px #90D5FF;
          ">EF CPA Shop
          </RouterLink>
        </div>
      </div>

      <div class="flex justify-center sm:justify-end mx-10">
        <div class="form-control mx-4 my-auto">
          <input type="text" v-model="searchText" placeholder="Search" class="input input-bordered flex p-2 rounded-lg"
            @keyup="handleEnter" />
        </div>
        <div class="">
          <div v-if="!isLoggedIn" @click="login" class="flex h-full items-center space-x-4">
            <RouterLink to="/register"
              class="btn btn-ghost border-none text-[#fff] hover:bg-transparent hover:text-white hover:shadow-none hover:border-none px-2 py-2">
              Register
            </RouterLink>
            <div
              class="btn btn-ghost border-none text-[#fff] hover:bg-transparent hover:text-white hover:shadow-none hover:border-none p-0 py-2">
              /</div>
            <div
              class="btn btn-ghost border-none text-[#fff] hover:bg-transparent hover:text-white hover:shadow-none hover:border-none px-2 py-2"
              @click="login">
              Login
            </div>
          </div>

          <div v-else class="dropdown dropdown-end">
            <label tabindex="0" class="btn btn-ghost btn-circle avatar">
              <div class="w-10 rounded-full">
                <img src="https://mikelopster.dev/mikelopster.da6b9a03.webp" />
              </div>
            </label>
            <ul tabindex="0" class="menu menu-sm dropdown-content mt-3 z-[1] p-2 shadow bg-base-100 rounded-lg w-52">
              <li>
                <RouterLink to="/profile" class="justify-between">
                  Profile
                </RouterLink>
              </li>
              <li>
                <a @click="logout">Logout</a>
              </li>
            </ul>
          </div>
        </div>
        <iconTheme class="ml-4" />
      </div>
    </div>


    <div class="navbar bg-warnning glass py-4 rounded-lg mt-1
     overflow-x-auto mx-auto">
      <div class="mx-auto text-currentColor">
        <ul class="flex flex-cols gap-2">
            <div class="box">
              <span class="borderline"></span>
              <!-- Button Content -->
                <li class="btn content py-4 px-4 text-lg font-thin border-transparent shadow-lg hover:bg-white/20 rounded-lg">
                  หน้าแรก
                </li>
            </div>
          <li class="btn border-none box w-24 py-4 px-4 text-lg font-thin">
            <span class="borderline"></span>
            <span class="content">
              หน้าแรก
            </span>
          </li>
          <li class="btn py-4 px-4 text-lg font-thin 
          bg-white/10 border-2 border-neutral/30
          shadow-lg backdrop-blur-md hover:bg-white/20 rounded-lg">
            เติมเกมส์
          </li>
          <li class="btn py-4 px-4 text-lg font-thin 
          bg-white/10 border-2 border-neutral/30
          shadow-lg backdrop-blur-md hover:bg-white/20 rounded-lg">
            เติมเงิน
          </li>
          <li class="btn py-4 px-4 text-lg font-thin 
          bg-white/10 border-2 border-neutral/30
          shadow-lg backdrop-blur-md hover:bg-white/20 rounded-lg">
            โปรโมชั่น
          </li>
          <li class="btn py-4 px-4 text-lg font-thin 
          bg-white/10 border-2 border-neutral/30
          shadow-lg backdrop-blur-md hover:bg-white/20 rounded-lg">
            ซื้อขาย ไอดีเกมส์
          </li>
          <li class="btn py-4 px-4 text-lg font-thin 
          bg-white/10 border-2 border-neutral/30
          shadow-lg backdrop-blur-md hover:bg-white/20 rounded-lg">
            บริการอื่นๆ
          </li>
        </ul>
      </div>

      <div class="flex">
        <!-- ตรงนี้แหละ เพิ่ม v-if เข้าไป -->

      </div>
    </div>

    <slot></slot>

    <footer class="footer p-10 bg-neutral text-neutral-content">
      <div>
        <span class="footer-title">Services</span>
        <a class="link link-hover">Branding</a>
        <a class="link link-hover">Design</a>
        <a class="link link-hover">Marketing</a>
        <a class="link link-hover">Advertisement</a>
      </div>
      <div>
        <span class="footer-title">Company</span>
        <a class="link link-hover">About us</a>
        <a class="link link-hover">Contact</a>
        <a class="link link-hover">Jobs</a>
        <a class="link link-hover">Press kit</a>
      </div>
      <div>
        <span class="footer-title">Legal</span>
        <a class="link link-hover">Terms of use</a>
        <a class="link link-hover">Privacy policy</a>
        <a class="link link-hover">Cookie policy</a>
      </div>
    </footer>
  </div>
</template>


<style scoped>
.box{
  position: relative;
  background: #000;
  border-radius: 4px;
  overflow: hidden;
}

.box::before {
  content: '';
  position: absolute;
  top: 50%;
  left: 50%;
  width: 100px;
  height: 100px;
  background: linear-gradient(0deg ,#ff2770, #ff2770, #ff2770 , transparent, transparent);
  animation : animate 6s linear infinite;
  transform-origin: top left;
}
.box::after{
  content: '';
  position: absolute;
  top: 50%;
  left: 50%;
  width: 100px;
  height: 100px;
  background: linear-gradient(0deg ,#ff2770, #ff2770, #ff2770, transparent, transparent);
  animation : animate 6s linear infinite;
  transform-origin: top left;
  animation-delay: -3s;
}
.borderline {
  position: absolute;
  top: 0;
  inset: 0;
}
.borderline::before {
  content: '';
  position: absolute;
  top: 50%;
  left: 50%;
  width: 100px;
  height: 100px;
  background: linear-gradient(0deg, #45f3ff, #45f3ff, #45f3ff , transparent, transparent);
  animation : animate 6s linear infinite;
  transform-origin: top left;
  animation-delay: -1.5s;
  z-index: 1;
}
.borderline::after {
  content: '';
  position: absolute;
  top: 50%;
  left: 50%;
  width: 100px;
  height: 100px;
  background: linear-gradient(0deg, #45f3ff, #45f3ff, #45f3ff , transparent, transparent);
  animation : animate 6s linear infinite;
  transform-origin: top left;
  animation-delay: -4.5s;
  z-index: 1;
}

@keyframes animate {
  0% {
    transform: rotate(0deg);
  } 
  100% {
    transform: rotate(360deg);
  }
}

.content {
  inset: 2px;
  position: absolute;
  z-index: 10;
  border-radius: 4px;
  overflow: hidden;
  display: flex;
  justify-content: center;
  align-items: center;
  background: #28292d;
  backdrop-filter: blur(8px);
}
.content::before {
  content: '';
  width: 120%;
  height: 120%;
  position: absolute;
  z-index: -1;
  border-radius: 4px;
  background: rgba(255, 255, 255, 0.3);
}
.content::after {
  content: '';
  width: 100%;
  height: 100%;
  position: absolute;
  z-index: -1;
  border-radius: 4px;
}
.content:hover{
  color: oklch(0.47 0.2104 329.41);
  z-index: 10;
}
/* Fix: This is how you target the ::after pseudo-element when the parent is hovered */
/* .content:hover::before {
  background: rgba(255, 255, 255, 0.3);
} */
.content:hover::after {
  color: oklch(0.47 0.2104 329.41);
  z-index: -1;
}
</style>