<template>
  <MainLayout>
    <div id="ItemPage" class="mt-4 max-w-[1200px] mx-auto px-2">
      <div class="md:flex gap-4 justify-between mx-auto w-full">
        <div class="md:w-[40%]">
          <img
            v-if="currentImage"
            class="rounded-lg object-fit"
            :src="currentImage" />
          <div
            v-if="images[0] !== ''"
            class="flex items-center justify-center mt-2">
            <div v-for="image in images">
              <img
                @mouseover="currentImage = image"
                @click="currentImage = image"
                width="70"
                class="rounded-md object-fit border-[3px] cursor-pointer"
                :class="currentImage === image ? 'border-accent-cinnbar' : ''"
                :src="image" />
            </div>
          </div>
        </div>
        <div class="md:w-[60%] bg-white p-3 rounded-lg">
          <div v-if="product && product.data">
            <p class="mb-2">{{ product.data.title }}</p>
            <p class="font-light text-[12px] mb-2">
              {{ product.data.description }}
            </p>
          </div>
          <div v-if="true">
            <p class="mb-2 text-xl font-bold text-secondary-oxford-blue">
              Title
            </p>
            <p class="font-light text-[12px] mb-2 text-lg">
              Lorem ipsum dolor sit amet consectetur adipiscing elit, porta
              malesuada imperdiet sociosqu porttitor eleifend, ut dui cum
              sollicitudin fusce id. Integer bibendum urna donec vivamus est
              duis dapibus euismod, mauris placerat lobortis habitasse varius
              ultricies massa molestie, eleifend nisl suscipit laoreet tincidunt
              cum semper. In magna neque duis ad etiam suscipit litora fermentum
              ligula fusce ut, massa nulla risus sed nam nisl facilisis placerat
              montes iaculis quam tempus, arcu dapibus praesent justo tincidunt
              posuere lacinia cum dictumst parturient.
            </p>
          </div>
          <div class="flex items-center pt-1.5">
            <span class="h-4 min-w-4 rounded-full p-0.5 bg-[#FFD000] mr-2">
              <Icon
                name="material-symbols:star-rounded"
                class="-mt-[17px]"
                size="12" />
            </span>
            <p class="text-acceborder-accent-cinnbar">Ahorra 5%</p>
          </div>
          <div class="flex items-center justify-start my-2">
            <Icon name="ic:baseline-star" color="#F4442E" />
            <Icon name="ic:baseline-star" color="#F4442E" />
            <Icon name="ic:baseline-star" color="#F4442E" />
            <Icon name="ic:baseline-star" color="#F4442E" />
            <Icon name="ic:baseline-star" color="#F4442E" />
            <span class="text-[13px] font-light ml-2"
              >5 213 Opiniones 1,000+ pedidos</span
            >
          </div>
          <div class="border-b" />
          <div class="flex items-center justify-start gap-2 my-2">
            <div class="text-xl font-bold">$ {{ priceComputed }}</div>
            <span
              class="bg-accent-baby-powder border text-[#C08562] text-[9px] font-semibold px-1.5 rounded-sm"
              >70% menos</span
            >
          </div>

          <div class="py-2" />
          <button
            @click="addToCart()"
            :disabled="isInCart"
            class="px-6 py-2 rounded-lg text-white text-lg font-semibold bg-gradient-to-r from-primary-fern-green to-primary-mantis">
            <div v-if="isInCart">Ya fue agregado</div>
            <div v-else>Agregar al carrito</div>
          </button>
        </div>
      </div>
    </div>
  </MainLayout>
</template>

<script setup>
import MainLayout from "~/layouts/MainLayout.vue";
import { useUserStore } from "~/stores/user";
const userStore = useUserStore();

const route = useRoute();

let product = ref(null);
let currentImage = ref(null);

// onBeforeMount(async () => {
//   product.value = await useFetch(
//     `/api/prisma/get-product-by-id/${route.params.id}`
//   );
// });

// watchEffect(() => {
//   if (product.value && product.value.data) {
//     currentImage.value = product.value.data.url;
//     images.value[0] = product.value.data.url;
//     userStore.isLoading = false;
//   }
// });

onMounted(() => {
  watchEffect(() => {
    currentImage.value =
      "https://coolinario.pe/sistema/pages/forms/productos/pilsen%206pack.jpg";
    images.value[0] =
      "https://coolinario.pe/sistema/pages/forms/productos/pilsen%206pack.jpg";
  });
});

const isInCart = computed(() => {
  let res = false;
  userStore.cart.forEach((prod) => {
    if (route.params.id == prod.id) {
      res = true;
    }
  });
  return res;
});

const priceComputed = computed(() => {
  if (product.value && product.value.data) {
    return product.value.data.price / 100;
  }
  return "26.00";
});

const images = ref([
  "",
  "https://coolinario.pe/sistema/pages/forms/productos/20205639.jpg",
  "https://coolinario.pe/sistema/pages/forms/productos/pilsen%20reto%20305ml.jpg",
  "https://coolinario.pe/sistema/pages/forms/productos/cusque%C3%B1a%20trigo%20310ml%20bot.jpg",
  "https://coolinario.pe/sistema/pages/forms/productos/948889.jpg",
  "https://picsum.photos/id/144/800/800",
]);

const addToCart = () => {
  //   userStore.cart.push(product.value.data);
  alert("Agregado");
};
</script>
