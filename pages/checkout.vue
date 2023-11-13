<template>
  <MainLayout>
    <div id="CheckoutPage" class="mt-4 max-w-[1200px] mx-auto px-2">
      <div class="md:flex gap-4 justify-between mx-auto w-full">
        <div class="md:w-[65%]">
          <div class="bg-white rounded-lg p-4">
            <div class="text-xl font-semibold mb-2">Dirección de envío</div>

            <div v-if="true">
              <NuxtLink
                to="/address"
                class="flex items-center pb-2 text-blue-500 hover:text-red-400">
                <Icon name="mdi:plus" size="18" class="mr-2" />
                Actualizar dirección
              </NuxtLink>

              <div class="pt-2 border-t">
                <div class="underline pb-1">Dirección de envío</div>
                <ul class="text-xs">
                  <li class="flex items-center gap-2">
                    <div>Contactame:</div>
                    <!-- <div class="font-bold">{{ currentAddress.data.name }}</div> -->
                  </li>
                  <li class="flex items-center gap-2">
                    <div>Dirección:</div>
                    <div class="font-bold">
                      <!-- {{ currentAddress.data.address }} -->
                    </div>
                  </li>
                  <li class="flex items-center gap-2">
                    <div>Departamento - Distrito:</div>
                    <!-- <div class="font-bold">{{ currentAddress.data.city }}</div> -->
                  </li>
                  <li class="flex items-center gap-2">
                    <div>Ciudad:</div>
                    <!-- <div class="font-bold">{{ currentAddress.data.city }}</div> -->
                  </li>
                </ul>
              </div>
            </div>

            <NuxtLink
              v-else
              to="/address"
              class="flex items-center text-blue-500 hover:text-red-400">
              <Icon name="mdi:plus" size="18" class="mr-2" />
              Agregar una nueva dirección
            </NuxtLink>
          </div>

          <div id="Items" class="bg-white rounded-lg p-4 mt-4">
            <div v-for="product in products">
              <CheckoutItem :product="product" />
            </div>
          </div>
        </div>

        <div class="md:hidden block my-4" />
        <div class="md:w-[35%]">
          <div id="PlaceOrder" class="bg-white rounded-lg p-4">
            <div class="text-2xl font-extrabold mb-2">Resumen</div>

            <div class="flex items-center justify-between my-4">
              <div class="">Envío Total</div>
              <div class="">Gratis</div>
            </div>

            <div class="border-t" />

            <div class="flex items-center justify-between my-4">
              <div class="font-semibold">Total</div>
              <div class="text-2xl font-semibold">
                $ <span class="font-extrabold">{{ total / 100 }}</span>
              </div>
            </div>

            <form @submit.prevent="pay()">
              <div
                class="border border-gray-500 p-2 rounded-sm"
                id="card-element" />

              <p
                id="card-error"
                role="alert"
                class="text-red-700 text-center font-semibold" />

              <button
                :disabled="isProcessing"
                type="submit"
                class="mt-4 bg-gradient-to-r from-primary-fern-green to-primary-mantis w-full text-white text-[21px] font-semibold p-1.5 rounded-full"
                :class="isProcessing ? 'opacity-70' : 'opacity-100'">
                <Icon v-if="isProcessing" name="eos-icons:loading" />
                <div v-else>Hacer el pedido</div>
              </button>
            </form>
          </div>

          <div class="bg-white rounded-lg p-4 mt-4">
            <div class="text-lg font-semibold mb-2 mt-2">TGTRON</div>
            <p class="my-2">
              TGTRON mantiene tu información y tus pagos seguros
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
const route = useRoute();

// definePageMeta({ middleware: "auth" });

let stripe = null;
let elements = null;
let card = null;
let form = null;
let total = ref(0);
let clientSecret = null;
let currentAddress = ref(null);
let isProcessing = ref(false);

// onBeforeMount(async () => {
//   if (userStore.checkout.length < 1) {
//     return navigateTo("/shoppingcart");
//   }

//   total.value = 0.0;
//   if (user.value) {
//     currentAddress.value = await useFetch(
//       `/api/prisma/get-address-by-user/${user.value.id}`
//     );
//     setTimeout(() => (userStore.isLoading = false), 200);
//   }
// });

// watchEffect(() => {
//   if (route.fullPath == "/checkout" && !user.value) {
//     return navigateTo("/auth");
//   }
// });

// onMounted(async () => {
//   isProcessing.value = true;

//   userStore.checkout.forEach((item) => {
//     total.value += item.price;
//   });
// });

// watch(
//   () => total.value,
//   () => {
//     if (total.value > 0) {
//       stripeInit();
//     }
//   }
// );

// const stripeInit = async () => {
//   const runtimeConfig = useRuntimeConfig();
//   stripe = Stripe(runtimeConfig.stripePk);

//   let res = await $fetch("/api/stripe/paymentintent", {
//     method: "POST",
//     body: {
//       amount: total.value,
//     },
//   });
//   clientSecret = res.client_secret;

//   elements = stripe.elements();
//   var style = {
//     base: {
//       fontSize: "18px",
//     },
//     invalid: {
//       fontFamily: "Arial, sans-serif",
//       color: "#EE4B2B",
//       iconColor: "#EE4B2B",
//     },
//   };
//   card = elements.create("card", {
//     hidePostalCode: true,
//     style: style,
//   });

//   // Stripe injects an iframe into the DOM
//   card.mount("#card-element");
//   card.on("change", function (event) {
//     // Disable the Pay button if there are no card details in the Element
//     document.querySelector("button").disabled = event.empty;
//     document.querySelector("#card-error").textContent = event.error
//       ? event.error.message
//       : "";
//   });

//   isProcessing.value = false;
// };

// const pay = async () => {
//   if (currentAddress.value && currentAddress.value.data == "") {
//     showError("Please add shipping address");
//     return;
//   }
//   isProcessing.value = true;

//   let result = await stripe.confirmCardPayment(clientSecret, {
//     payment_method: { card: card },
//   });

//   if (result.error) {
//     showError(result.error.message);
//     isProcessing.value = false;
//   } else {
//     await createOrder(result.paymentIntent.id);
//     userStore.cart = [];
//     userStore.checkout = [];
//     setTimeout(() => {
//       return navigateTo("/success");
//     }, 500);
//   }
// };

// const createOrder = async (stripeId) => {
//   await useFetch("/api/prisma/create-order", {
//     method: "POST",
//     body: {
//       userId: user.value.id,
//       stripeId: stripeId,
//       name: currentAddress.value.data.name,
//       address: currentAddress.value.data.address,
//       zipcode: currentAddress.value.data.zipcode,
//       city: currentAddress.value.data.city,
//       country: currentAddress.value.data.country,
//       products: userStore.checkout,
//     },
//   });
// };

const showError = (errorMsgText) => {
  let errorMsg = document.querySelector("#card-error");

  errorMsg.textContent = errorMsgText;
  setTimeout(() => {
    errorMsg.textContent = "";
  }, 4000);
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
