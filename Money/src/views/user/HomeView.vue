<script setup>
import { onMounted } from 'vue'
import { useRouter } from 'vue-router'

import { useUserProductStore } from '@/stores/user/product'

import UserLayout from '@/components/layouts/UserLayout.vue'
import Banner from '@/components/banner.vue'
// import ProductList from '@/components/ProductList.vue'

const userProductStore = useUserProductStore()

const router = useRouter()

onMounted(() => {
  userProductStore.loadProduct()
})

</script>

<template>
  <UserLayout>
    <div class="container mx-auto">
      <Banner class="my-2"/>
    
      <ProductList
        :products="userProductStore.list"
      >
      </ProductList>
    </div>
  </UserLayout>
</template>