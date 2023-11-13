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
    description:
      "Lorem ipsum dolor sit amet consectetur adipiscing elit, porta malesuada imperdiet sociosqu porttitor eleifend, ut dui cum sollicitudin fusce id. Integer bibendum urna donec vivamus est duis dapibus euismod, mauris placerat lobortis habitasse varius ultricies massa molestie, eleifend nisl suscipit laoreet tincidunt cum semper. In magna neque duis ad etiam suscipit litora fermentum ligula fusce ut, massa nulla risus sed nam nisl facilisis placerat montes iaculis quam tempus, arcu dapibus praesent justo tincidunt posuere lacinia cum dictumst parturient.",
    url: "https://coolinario.pe/sistema/pages/forms/productos/pilsen%206pack.jpg",
    price: 9999,
  },
  {
    id: 2,
    title: "Title 2",
    description:
      "Lorem ipsum dolor sit amet consectetur adipiscing elit, porta malesuada imperdiet sociosqu porttitor eleifend, ut dui cum sollicitudin fusce id. Integer bibendum urna donec vivamus est duis dapibus euismod, mauris placerat lobortis habitasse varius ultricies massa molestie, eleifend nisl suscipit laoreet tincidunt cum semper. In magna neque duis ad etiam suscipit litora fermentum ligula fusce ut, massa nulla risus sed nam nisl facilisis placerat montes iaculis quam tempus, arcu dapibus praesent justo tincidunt posuere lacinia cum dictumst parturient.",
    url: "https://coolinario.pe/sistema/pages/forms/productos/ondas%20picantes%20150G.jpg",
    price: 9999,
  },
  {
    id: 3,
    title: "Title 3",
    description:
      "Lorem ipsum dolor sit amet consectetur adipiscing elit, porta malesuada imperdiet sociosqu porttitor eleifend, ut dui cum sollicitudin fusce id. Integer bibendum urna donec vivamus est duis dapibus euismod, mauris placerat lobortis habitasse varius ultricies massa molestie, eleifend nisl suscipit laoreet tincidunt cum semper. In magna neque duis ad etiam suscipit litora fermentum ligula fusce ut, massa nulla risus sed nam nisl facilisis placerat montes iaculis quam tempus, arcu dapibus praesent justo tincidunt posuere lacinia cum dictumst parturient.",
    url: "https://coolinario.pe/sistema/pages/forms/productos/cricketspica150%20(1).jpg",
    price: 9999,
  },
  {
    id: 4,
    title: "Title 4",
    description:
      "Lorem ipsum dolor sit amet consectetur adipiscing elit, porta malesuada imperdiet sociosqu porttitor eleifend, ut dui cum sollicitudin fusce id. Integer bibendum urna donec vivamus est duis dapibus euismod, mauris placerat lobortis habitasse varius ultricies massa molestie, eleifend nisl suscipit laoreet tincidunt cum semper. In magna neque duis ad etiam suscipit litora fermentum ligula fusce ut, massa nulla risus sed nam nisl facilisis placerat montes iaculis quam tempus, arcu dapibus praesent justo tincidunt posuere lacinia cum dictumst parturient.",
    url: "https://coolinario.pe/sistema/pages/forms/productos/PASSPORT%20COMBO.jpg",
    price: 9999,
  },
  {
    id: 5,
    title: "Title 5",
    description:
      "Lorem ipsum dolor sit amet consectetur adipiscing elit, porta malesuada imperdiet sociosqu porttitor eleifend, ut dui cum sollicitudin fusce id. Integer bibendum urna donec vivamus est duis dapibus euismod, mauris placerat lobortis habitasse varius ultricies massa molestie, eleifend nisl suscipit laoreet tincidunt cum semper. In magna neque duis ad etiam suscipit litora fermentum ligula fusce ut, massa nulla risus sed nam nisl facilisis placerat montes iaculis quam tempus, arcu dapibus praesent justo tincidunt posuere lacinia cum dictumst parturient.",
    url: "https://coolinario.pe/sistema/pages/forms/productos/IGLU%20SOMET.jpg",
    price: 9999,
  },
  {
    id: 6,
    title: "Title 6",
    description:
      "Lorem ipsum dolor sit amet consectetur adipiscing elit, porta malesuada imperdiet sociosqu porttitor eleifend, ut dui cum sollicitudin fusce id. Integer bibendum urna donec vivamus est duis dapibus euismod, mauris placerat lobortis habitasse varius ultricies massa molestie, eleifend nisl suscipit laoreet tincidunt cum semper. In magna neque duis ad etiam suscipit litora fermentum ligula fusce ut, massa nulla risus sed nam nisl facilisis placerat montes iaculis quam tempus, arcu dapibus praesent justo tincidunt posuere lacinia cum dictumst parturient.",
    url: "https://coolinario.pe/sistema/pages/forms/productos/Ritz-Original-22-Web.jpg",
    price: 9999,
  },
  {
    id: 7,
    title: "Title 7",
    description:
      "Lorem ipsum dolor sit amet consectetur adipiscing elit, porta malesuada imperdiet sociosqu porttitor eleifend, ut dui cum sollicitudin fusce id. Integer bibendum urna donec vivamus est duis dapibus euismod, mauris placerat lobortis habitasse varius ultricies massa molestie, eleifend nisl suscipit laoreet tincidunt cum semper. In magna neque duis ad etiam suscipit litora fermentum ligula fusce ut, massa nulla risus sed nam nisl facilisis placerat montes iaculis quam tempus, arcu dapibus praesent justo tincidunt posuere lacinia cum dictumst parturient.",
    url: "https://coolinario.pe/sistema/pages/forms/productos/153249.jpg",
    price: 9999,
  },
  {
    id: 8,
    title: "Title 8",
    description:
      "Lorem ipsum dolor sit amet consectetur adipiscing elit, porta malesuada imperdiet sociosqu porttitor eleifend, ut dui cum sollicitudin fusce id. Integer bibendum urna donec vivamus est duis dapibus euismod, mauris placerat lobortis habitasse varius ultricies massa molestie, eleifend nisl suscipit laoreet tincidunt cum semper. In magna neque duis ad etiam suscipit litora fermentum ligula fusce ut, massa nulla risus sed nam nisl facilisis placerat montes iaculis quam tempus, arcu dapibus praesent justo tincidunt posuere lacinia cum dictumst parturient.",
    url: "https://coolinario.pe/sistema/pages/forms/productos/pilsen%206pack.jpg",
    price: 9999,
  },
  {
    id: 9,
    title: "Title 9",
    description:
      "Lorem ipsum dolor sit amet consectetur adipiscing elit, porta malesuada imperdiet sociosqu porttitor eleifend, ut dui cum sollicitudin fusce id. Integer bibendum urna donec vivamus est duis dapibus euismod, mauris placerat lobortis habitasse varius ultricies massa molestie, eleifend nisl suscipit laoreet tincidunt cum semper. In magna neque duis ad etiam suscipit litora fermentum ligula fusce ut, massa nulla risus sed nam nisl facilisis placerat montes iaculis quam tempus, arcu dapibus praesent justo tincidunt posuere lacinia cum dictumst parturient.",
    url: "https://coolinario.pe/sistema/pages/forms/productos/ondas%20picantes%20150G.jpg",
    price: 9999,
  },
  {
    id: 10,
    title: "Title 10",
    description:
      "Lorem ipsum dolor sit amet consectetur adipiscing elit, porta malesuada imperdiet sociosqu porttitor eleifend, ut dui cum sollicitudin fusce id. Integer bibendum urna donec vivamus est duis dapibus euismod, mauris placerat lobortis habitasse varius ultricies massa molestie, eleifend nisl suscipit laoreet tincidunt cum semper. In magna neque duis ad etiam suscipit litora fermentum ligula fusce ut, massa nulla risus sed nam nisl facilisis placerat montes iaculis quam tempus, arcu dapibus praesent justo tincidunt posuere lacinia cum dictumst parturient.",
    url: "https://coolinario.pe/sistema/pages/forms/productos/cricketspica150%20(1).jpg",
    price: 9999,
  },
  {
    id: 11,
    title: "Title 11",
    description:
      "Lorem ipsum dolor sit amet consectetur adipiscing elit, porta malesuada imperdiet sociosqu porttitor eleifend, ut dui cum sollicitudin fusce id. Integer bibendum urna donec vivamus est duis dapibus euismod, mauris placerat lobortis habitasse varius ultricies massa molestie, eleifend nisl suscipit laoreet tincidunt cum semper. In magna neque duis ad etiam suscipit litora fermentum ligula fusce ut, massa nulla risus sed nam nisl facilisis placerat montes iaculis quam tempus, arcu dapibus praesent justo tincidunt posuere lacinia cum dictumst parturient.",
    url: "https://coolinario.pe/sistema/pages/forms/productos/PASSPORT%20COMBO.jpg",
    price: 9999,
  },
  {
    id: 12,
    title: "Title 12",
    description:
      "Lorem ipsum dolor sit amet consectetur adipiscing elit, porta malesuada imperdiet sociosqu porttitor eleifend, ut dui cum sollicitudin fusce id. Integer bibendum urna donec vivamus est duis dapibus euismod, mauris placerat lobortis habitasse varius ultricies massa molestie, eleifend nisl suscipit laoreet tincidunt cum semper. In magna neque duis ad etiam suscipit litora fermentum ligula fusce ut, massa nulla risus sed nam nisl facilisis placerat montes iaculis quam tempus, arcu dapibus praesent justo tincidunt posuere lacinia cum dictumst parturient.",
    url: "https://coolinario.pe/sistema/pages/forms/productos/IGLU%20SOMET.jpg",
    price: 9999,
  },
  {
    id: 13,
    title: "Title 13",
    description:
      "Lorem ipsum dolor sit amet consectetur adipiscing elit, porta malesuada imperdiet sociosqu porttitor eleifend, ut dui cum sollicitudin fusce id. Integer bibendum urna donec vivamus est duis dapibus euismod, mauris placerat lobortis habitasse varius ultricies massa molestie, eleifend nisl suscipit laoreet tincidunt cum semper. In magna neque duis ad etiam suscipit litora fermentum ligula fusce ut, massa nulla risus sed nam nisl facilisis placerat montes iaculis quam tempus, arcu dapibus praesent justo tincidunt posuere lacinia cum dictumst parturient.",
    url: "https://coolinario.pe/sistema/pages/forms/productos/Ritz-Original-22-Web.jpg",
    price: 9999,
  },
  {
    id: 14,
    title: "Title 14",
    description:
      "Lorem ipsum dolor sit amet consectetur adipiscing elit, porta malesuada imperdiet sociosqu porttitor eleifend, ut dui cum sollicitudin fusce id. Integer bibendum urna donec vivamus est duis dapibus euismod, mauris placerat lobortis habitasse varius ultricies massa molestie, eleifend nisl suscipit laoreet tincidunt cum semper. In magna neque duis ad etiam suscipit litora fermentum ligula fusce ut, massa nulla risus sed nam nisl facilisis placerat montes iaculis quam tempus, arcu dapibus praesent justo tincidunt posuere lacinia cum dictumst parturient.",
    url: "https://coolinario.pe/sistema/pages/forms/productos/153249.jpg",
    price: 9999,
  },
  {
    id: 15,
    title: "Title 15",
    description:
      "Lorem ipsum dolor sit amet consectetur adipiscing elit, porta malesuada imperdiet sociosqu porttitor eleifend, ut dui cum sollicitudin fusce id. Integer bibendum urna donec vivamus est duis dapibus euismod, mauris placerat lobortis habitasse varius ultricies massa molestie, eleifend nisl suscipit laoreet tincidunt cum semper. In magna neque duis ad etiam suscipit litora fermentum ligula fusce ut, massa nulla risus sed nam nisl facilisis placerat montes iaculis quam tempus, arcu dapibus praesent justo tincidunt posuere lacinia cum dictumst parturient.",
    url: "https://coolinario.pe/sistema/pages/forms/productos/pilsen%206pack.jpg",
    price: 9999,
  },
  {
    id: 16,
    title: "Title 16",
    description:
      "Lorem ipsum dolor sit amet consectetur adipiscing elit, porta malesuada imperdiet sociosqu porttitor eleifend, ut dui cum sollicitudin fusce id. Integer bibendum urna donec vivamus est duis dapibus euismod, mauris placerat lobortis habitasse varius ultricies massa molestie, eleifend nisl suscipit laoreet tincidunt cum semper. In magna neque duis ad etiam suscipit litora fermentum ligula fusce ut, massa nulla risus sed nam nisl facilisis placerat montes iaculis quam tempus, arcu dapibus praesent justo tincidunt posuere lacinia cum dictumst parturient.",
    url: "https://coolinario.pe/sistema/pages/forms/productos/ondas%20picantes%20150G.jpg",
    price: 9999,
  },
  {
    id: 17,
    title: "Title 17",
    description:
      "Lorem ipsum dolor sit amet consectetur adipiscing elit, porta malesuada imperdiet sociosqu porttitor eleifend, ut dui cum sollicitudin fusce id. Integer bibendum urna donec vivamus est duis dapibus euismod, mauris placerat lobortis habitasse varius ultricies massa molestie, eleifend nisl suscipit laoreet tincidunt cum semper. In magna neque duis ad etiam suscipit litora fermentum ligula fusce ut, massa nulla risus sed nam nisl facilisis placerat montes iaculis quam tempus, arcu dapibus praesent justo tincidunt posuere lacinia cum dictumst parturient.",
    url: "https://coolinario.pe/sistema/pages/forms/productos/cricketspica150%20(1).jpg",
    price: 9999,
  },
  {
    id: 18,
    title: "Title 18",
    description:
      "Lorem ipsum dolor sit amet consectetur adipiscing elit, porta malesuada imperdiet sociosqu porttitor eleifend, ut dui cum sollicitudin fusce id. Integer bibendum urna donec vivamus est duis dapibus euismod, mauris placerat lobortis habitasse varius ultricies massa molestie, eleifend nisl suscipit laoreet tincidunt cum semper. In magna neque duis ad etiam suscipit litora fermentum ligula fusce ut, massa nulla risus sed nam nisl facilisis placerat montes iaculis quam tempus, arcu dapibus praesent justo tincidunt posuere lacinia cum dictumst parturient.",
    url: "https://coolinario.pe/sistema/pages/forms/productos/PASSPORT%20COMBO.jpg",
    price: 9999,
  },
  {
    id: 19,
    title: "Title 19",
    description:
      "Lorem ipsum dolor sit amet consectetur adipiscing elit, porta malesuada imperdiet sociosqu porttitor eleifend, ut dui cum sollicitudin fusce id. Integer bibendum urna donec vivamus est duis dapibus euismod, mauris placerat lobortis habitasse varius ultricies massa molestie, eleifend nisl suscipit laoreet tincidunt cum semper. In magna neque duis ad etiam suscipit litora fermentum ligula fusce ut, massa nulla risus sed nam nisl facilisis placerat montes iaculis quam tempus, arcu dapibus praesent justo tincidunt posuere lacinia cum dictumst parturient.",
    url: "https://coolinario.pe/sistema/pages/forms/productos/IGLU%20SOMET.jpg",
    price: 9999,
  },
  {
    id: 20,
    title: "Title 20",
    description:
      "Lorem ipsum dolor sit amet consectetur adipiscing elit, porta malesuada imperdiet sociosqu porttitor eleifend, ut dui cum sollicitudin fusce id. Integer bibendum urna donec vivamus est duis dapibus euismod, mauris placerat lobortis habitasse varius ultricies massa molestie, eleifend nisl suscipit laoreet tincidunt cum semper. In magna neque duis ad etiam suscipit litora fermentum ligula fusce ut, massa nulla risus sed nam nisl facilisis placerat montes iaculis quam tempus, arcu dapibus praesent justo tincidunt posuere lacinia cum dictumst parturient.",
    url: "https://coolinario.pe/sistema/pages/forms/productos/Ritz-Original-22-Web.jpg",
    price: 9999,
  },
  {
    id: 21,
    title: "Title 21",
    description:
      "Lorem ipsum dolor sit amet consectetur adipiscing elit, porta malesuada imperdiet sociosqu porttitor eleifend, ut dui cum sollicitudin fusce id. Integer bibendum urna donec vivamus est duis dapibus euismod, mauris placerat lobortis habitasse varius ultricies massa molestie, eleifend nisl suscipit laoreet tincidunt cum semper. In magna neque duis ad etiam suscipit litora fermentum ligula fusce ut, massa nulla risus sed nam nisl facilisis placerat montes iaculis quam tempus, arcu dapibus praesent justo tincidunt posuere lacinia cum dictumst parturient.",
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
