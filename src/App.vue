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
    <v-btn v-show="showLogout" @click="authStore.logout()" color="transparent text-white mb-5" elevation="0">Logout</v-btn>
  </v-app>
</template>

<script setup lang="ts">
  import {computed, Ref, ref, watch} from 'vue'
  import {useCommonStore} from "./stores/useCommonStore";
  import {useAuthStore} from "./stores/useAuthStore";

  const commonStore = useCommonStore()
  const authStore = useAuthStore()
  const snackbar: Ref<boolean> = ref(false);
  const snackbarText: Ref<string> = computed(() => commonStore.snackbarText);
  const showLogout = computed(() => authStore.user)

  watch(snackbarText, () => snackbar.value = true);
</script>
<style>
  .bgApp {
    background-color: #5c3551ff !important;
  }
</style>