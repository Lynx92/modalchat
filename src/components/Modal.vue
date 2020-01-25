<template>
  <q-card>
    <q-toolbar class="border-bottom">
      <q-toolbar-title class="text-center">
        <span class="text-weight-bold">Comentarios</span>
      </q-toolbar-title>

      <q-btn color="primary" flat round dense icon="close" v-close-popup />
    </q-toolbar>

    <q-card-section>
      <Chat />
    </q-card-section>
  </q-card>
</template>

<script>
import Chat from "./Chat";
export default {
  name: "Modal",
  components: {
    Chat
  }
};
</script>

<style>
.border-bottom {
  border-bottom: 2px solid black;
}
</style>
