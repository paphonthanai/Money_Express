<script setup>
import { onMounted } from 'vue'
import { useRouter } from 'vue-router'

import { useUserProductStore } from '@/stores/user/product'

import UserLayout from '@/components/layouts/UserLayout.vue'
import Banner from '@/components/banner.vue'
import MenuBar from '@/components/MenuBar.vue'
import SPECIALOFFER from '@/components/SPECIALOFFER.vue'

const userProductStore = useUserProductStore()

const router = useRouter()

onMounted(() => {

})

</script>

<template>
  <UserLayout>
    <Banner class="my-2"/>
    <div class="section1 container w-full mx-auto">
      <div class="w-full mx-auto">
        <MenuBar class="mx-auto my-2"/>
      </div>
      <div class="w-full">
        <SPECIALOFFER />
      </div>
    </div>
    <div class="section2 container mx-auto">
      <ProductList
        :products="userProductStore.list"
      >
      </ProductList>
    </div>
  </UserLayout>
</template>