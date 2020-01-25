<template>
  <div class="home">
    <q-btn label="Comentarios" color="primary" @click="toolbar = true" />
    <q-dialog v-model="toolbar" persistent>
      <Modal />
    </q-dialog>
  </div>
</template>

<script>
import Modal from "./Modal";
export default {
  name: "Home",
  components: {
    Modal
  },
  data: () => ({
    toolbar: false
  })
};
</script>

<style scoped lang="scss">
.home {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100vw;
  height: 85vh;
}
</style>
