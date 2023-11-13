<template>
  <MainLayout>
    <div id="AddressPage" class="mt-4 max-w-[500px] mx-auto px-2">
      <div class="mx-auto bg-white rounded-lg p-3">
        <div class="text-xl text-bold mb-2">Detalle de la dirección</div>
        <form @submit.prevent="submit()">
          <TextInput
            class="w-full"
            placeholder="Nombre"
            v-model:input="nombre"
            inputType="text"
            :error="error && error.type == 'nombre' ? error.message : ''" />

          <TextInput
            class="w-full mt-2"
            placeholder="Dirección"
            v-model:input="address"
            inputType="text"
            :error="error && error.type == 'address' ? error.message : ''" />

          <TextInput
            class="w-full mt-2"
            placeholder="Departamento - Distrito"
            v-model:input="DepDist"
            inputType="text"
            :error="error && error.type == 'DepDist' ? error.message : ''" />
          <TextInput
            class="w-full mt-2"
            placeholder="Ciudad"
            v-model:input="city"
            inputType="text"
            :error="error && error.type == 'DepDist' ? error.message : ''" />

          <button
            :disabled="isWorking"
            type="submit"
            class="mt-6 bg-gradient-to-r from-primary-fern-green to-primary-mantis w-full text-white text-[21px] font-semibold p-1.5 rounded-full">
            <div v-if="!isWorking">Actualizar Dirección</div>
            <Icon v-else name="eos-icons:loading" size="25" class="mr-2" />
          </button>
        </form>
      </div>
    </div>
  </MainLayout>
</template>

<script setup>
import MainLayout from "~/layouts/MainLayout.vue";
import { useUserStore } from "~/stores/user";
const userStore = useUserStore();

let nombre = ref(null);
let address = ref(null);
let DepDist = ref(null);
let country = ref(null);

let currentAddress = ref(null);
let isUpdate = ref(false);
let isWorking = ref(false);
let error = ref(null);

watchEffect(async () => {
  userStore.isLoading = false;
});

const submit = async () => {
  isWorking.value = true;
  error.value = null;

  if (!nombre.value) {
    error.value = {
      type: "nombre",
      message: "El nombre es requerido",
    };
  } else if (!address.value) {
    error.value = {
      type: "address",
      message: "La dirección es requerida",
    };
  } else if (!DepDist.value) {
    error.value = {
      type: "DepDist",
      message: "El departamento - distrito es requerido",
    };
  } else if (!country.value) {
    error.value = {
      type: "country",
      message: "La ciudad es requerida",
    };
  }

  if (error.value) {
    isWorking.value = false;
    return;
  }

  isWorking.value = false;

  return navigateTo("/checkout");
};
</script>
