<template>
  <MainLayout>
    <div id="ShoppingCartPage" class="mt-4 max-w-[1200px] mx-auto px-2">
      <div v-if="false" class="h-[500px] flex items-center justify-center">
        <div class="pt-20">
          <img class="mx-auto" width="250" src="/cart-empty.png" />

          <div class="text-xl text-center mt-4">No tienes ningún producto?</div>

          <div v-if="true" class="flex text-center">
            <NuxtLink
              to="/auth"
              class="bg-primary-mantis w-full text-white text-[21px] font-semibold p-1.5 rounded-full mt-4">
              Iniciar Sesión
            </NuxtLink>
          </div>
        </div>
      </div>

      <div v-else class="md:flex gap-4 justify-between mx-auto w-full">
        <div class="md:w-[65%]">
          <div class="bg-white rounded-lg p-4">
            <div class="text-2xl font-bold mb-2">
              Carrito de compras ({{ userStore.cart.length }})
            </div>
          </div>

          <div id="Items" class="bg-white rounded-lg p-4 mt-4">
            <div v-for="product in products">
              <CartItem
                :product="product"
                :selectedArray="selectedArray"
                @selectedRadio="selectedRadioFunc" />
            </div>
          </div>
        </div>

        <div class="md:hidden block my-4" />
        <div class="md:w-[35%]">
          <div id="Summary" class="bg-white rounded-lg p-4">
            <div class="text-2xl font-extrabold mb-2">Resumen</div>
            <div class="flex items-center justify-between my-4">
              <div class="font-semibold">Total</div>
              <div class="text-2xl font-semibold">
                $ <span class="font-extrabold">{{ totalPriceComputed }}</span>
              </div>
            </div>
            <button
              @click="goToCheckout"
              class="flex items-center justify-center bg-accent-cinnbar w-full text-white text-[21px] font-semibold p-1.5 rounded-full mt-4">
              Pagar
            </button>
          </div>

          <div id="PaymentProtection" class="bg-white rounded-lg p-4 mt-4">
            <div class="text-lg font-semibold mb-2">Métodos de pago</div>
            <div class="flex items-center justify-start gap-8 my-4">
              <div v-for="card in cards">
                <img class="h-6" :src="card" />
              </div>
            </div>

            <div class="border-b" />

            <div class="text-lg font-semibold mb-2 mt-2">
              Protección al cliente
            </div>
            <p class="my-2">
              Obtenga un reembolso completo si el artículo no es como se
              describe o si no lo es entregado
            </p>
          </div>
        </div>
      </div>
    </div>
  </MainLayout>
</template>

<script setup>
import MainLayout from "~/layouts/MainLayout.vue";
import { useUserStore } from "~/stores/user";
const userStore = useUserStore();

let selectedArray = ref([]);

onMounted(() => {
  setTimeout(() => (userStore.isLoading = false), 200);
});

const cards = ref(["visa.png", "mastercard.png", "paypal.png", "applepay.png"]);

const totalPriceComputed = computed(() => {
  let price = 0;
  userStore.cart.forEach((prod) => {
    price += prod.price;
  });
  return price / 100;
});

const selectedRadioFunc = (e) => {
  if (!selectedArray.value.length) {
    selectedArray.value.push(e);
    return;
  }

  selectedArray.value.forEach((item, index) => {
    if (e.id != item.id) {
      selectedArray.value.push(e);
    } else {
      selectedArray.value.splice(index, 1);
    }
  });
};

const goToCheckout = () => {
  let ids = [];
  userStore.checkout = [];

  selectedArray.value.forEach((item) => ids.push(item.id));

  let res = userStore.cart.filter((item) => {
    return ids.indexOf(item.id) != -1;
  });

  res.forEach((item) => userStore.checkout.push(toRaw(item)));

  return navigateTo("/checkout");
};

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
];
</script>
