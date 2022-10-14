<template>
  <v-app class="bgApp">
    <v-main>
      <v-fade-transition mode="out-in">
        <router-view/>
      </v-fade-transition>
    </v-main>
    <v-snackbar v-model="snackbar">
      {{ snackbarText }}
      <template v-slot:actions>
        <v-btn
            color="red"
            variant="text"
            @click="snackbar = false">
          Close
        </v-btn>
      </template>
    </v-snackbar>
    <v-btn @click="logout" color="transparent text-white mb-5" elevation="0">Logout</v-btn>
  </v-app>
</template>

<script setup lang="ts">
  import {computed, Ref, ref, watch} from 'vue'
  import {useCommonStore} from "./stores/useCommonStore";
  import router from "./router";

  const commonStore = useCommonStore()
  const snackbar: Ref<boolean> = ref(false);
  const snackbarText: Ref<string> = computed(() => commonStore.snackbarText);

  const logout = () => {
    localStorage.removeItem('tipoUsuario')
    localStorage.removeItem('dataHoraExpiracao')
    localStorage.removeItem('tokenAcesso')
    router.push('/login')
  }
  watch(snackbarText, () => snackbar.value = true);
</script>
<style>
  .bgApp {
    background-color: #5c3551ff !important;
  }
</style>