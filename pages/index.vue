<template>
  <MainLayout>
    <div id="IndexPage" class="mt-4 max-w-[1200px] mx-auto px-2">
      <div
        class="grid xl:grid-cols-6 lg:grid-cols-5 md:grid-cols-4 sm:grid-cols-3 grid-cols-2 gap-4">
        <div v-if="products" v-for="product in products" :key="product">
          <ProductComponent :product="product" />
        </div>
      </div>
    </div>
  </MainLayout>
</template>

<script setup>
import MainLayout from "../layouts/MainLayout.vue";

const products = [
  {
    id: 1,
    title: "Title 1",
    description: "This is a description",
    url: "https://coolinario.pe/sistema/pages/forms/productos/pilsen%206pack.jpg",
    price: 9999,
  },
  {
    id: 2,
    title: "Title 2",
    description: "This is a description",
    url: "https://coolinario.pe/sistema/pages/forms/productos/ondas%20picantes%20150G.jpg",
    price: 9999,
  },
  {
    id: 3,
    title: "Title 3",
    description: "This is a description",
    url: "https://coolinario.pe/sistema/pages/forms/productos/cricketspica150%20(1).jpg",
    price: 9999,
  },
  {
    id: 4,
    title: "Title 4",
    description: "This is a description",
    url: "https://coolinario.pe/sistema/pages/forms/productos/PASSPORT%20COMBO.jpg",
    price: 9999,
  },
  {
    id: 5,
    title: "Title 5",
    description: "This is a description",
    url: "https://coolinario.pe/sistema/pages/forms/productos/IGLU%20SOMET.jpg",
    price: 9999,
  },
  {
    id: 6,
    title: "Title 6",
    description: "This is a description",
    url: "https://coolinario.pe/sistema/pages/forms/productos/Ritz-Original-22-Web.jpg",
    price: 9999,
  },
  {
    id: 7,
    title: "Title 7",
    description: "This is a description",
    url: "https://coolinario.pe/sistema/pages/forms/productos/153249.jpg",
    price: 9999,
  },
];
// import { useUserStore } from '~/stores/user';
// const userStore = useUserStore()

// let products = ref(null)
// onBeforeMount(async () => {
//     products.value = await useFetch('/api/prisma/get-all-products')
//     setTimeout(() => userStore.isLoading = false, 1000)
// })
</script>
