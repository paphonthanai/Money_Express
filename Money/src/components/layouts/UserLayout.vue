<script setup>
import { ref, onMounted } from 'vue'
import { RouterLink, useRouter } from 'vue-router'


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
    <div
      class="grid grid-cols-2 items-center h-24 py-1 space-between bg-gradient-to-r from-[#350534] via-[#940691] to-[#350534]">
      <div class="text-[#fff]">
        <div class="flex-1">
          <RouterLink to="/" class="
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

      <div class="flex justify-end mx-10">
        <div class="form-control mx-4">
          <input type="text" v-model="searchText" placeholder="Search" class="input input-bordered w-24 md:w-auto"
            @keyup="handleEnter" />
        </div>
        <div class="">
          <div v-if="!isLoggedIn" @click="login" class="flex items-center space-x-4">
            <RouterLink to="/register"
              class="btn btn-ghost text-[#fff] hover:bg-transparent hover:text-white hover:shadow-none hover:border-none px-2">
              Register
            </RouterLink>
            <div
              class="btn btn-ghost text-[#fff] hover:bg-transparent hover:text-white hover:shadow-none hover:border-none p-0">
              /</div>
            <div
              class="btn btn-ghost text-[#fff] hover:bg-transparent hover:text-white hover:shadow-none hover:border-none px-2"
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
            <ul tabindex="0" class="menu menu-sm dropdown-content mt-3 z-[1] p-2 shadow bg-base-100 rounded-box w-52">
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
      </div>
    </div>
    <div class="navbar bg-[#121D3D]">
      <div class="mx-auto text-[#fff]">
        <ul class="flex flex-cols gap-2">
          <li class="btn glass backdrop-blur-md
           bg-white/0 border border-white/20 rounded-md">
            หน้าหลัก
          </li>
          <li class="btn glass backdrop-blur-md 
          bg-white/0 border border-white/20 rounded-md">
            เติมเกมส์
          </li>
          <li class="btn glass backdrop-blur-md 
          bg-white/0 border border-white/20 rounded-md">
            เติมเงิน
          </li>
          <li class="btn glass backdrop-blur-md 
          bg-white/0 border border-white/20 rounded-md">
            โปรโมชั่น
          </li>
          <li class="btn glass backdrop-blur-md 
          bg-white/0 border border-white/20 rounded-md">
            ซื้อขาย ไอดีเกมส์
          </li>
          <li class="btn glass backdrop-blur-md 
          bg-white/0 border border-white/20 rounded-md">
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
        <span class="footer-title">บริการ</span>
        <a class="link link-hover">หน้าแรก</a>
        <a class="link link-hover">เติมเกมส์</a>
        <a class="link link-hover">เติมเงิน</a>
        <a class="link link-hover">ซื้อ-ขาย ไอดีเกมส์</a>
      </div>
      <div>
        <span class="footer-title">Company</span>
        <a class="link link-hover">เกี่ยวกับเรา</a>
        <a class="link link-hover">
          ติดต่อ
        </a>
        <a class="link link-hover">บริการอื่นๆ</a>
      </div>
      <div>
        <span class="footer-title">เกี่ยวกับกฎหมาย</span>
        <a class="link link-hover">
          เงื่อนไขการใช้งาน
        </a>
        <a class="link link-hover">นโยบายความเป็นส่วนตัว</a>
        <a class="link link-hover">นโยบายคุกกี้</a>
      </div>
    </footer>
    <div class="w-full bg-base-300 text-center py-4 text-sm text-gray-500">
      © Copyright PNJ Tech.Co.,Ltd. All rights reserved.</div>
  </div>
</template>