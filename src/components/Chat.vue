<template>
  <div>
    <ul>
      <li v-for="(message, idx) in messages" :key="idx">
        <div v-if="message.type == 'document'" :class="message.type">
          <div class="text">
            <p class="text-bold">VERSIÓN {{ message.version }}</p>
            <p class="text-bold text-primary">{{ message.text }}</p>
            <p class="q-gutter-x-md">
              <span>Documento/PDF ({{ message.size }})</span>
              <span>{{ message.date }}</span>
            </p>
          </div>
          <div class="avatar">
            <q-icon name="cloud_download" size="xl" color="primary" />
          </div>
        </div>

        <div v-else-if="message.type == 'receive'" :class="message.type">
          <q-chat-message
            avatar="https://cdn.quasar.dev/img/avatar2.jpg"
            :text="[message.text]"
            :stamp="message.date"
            text-color="black"
            bg-color="grey-3"
          />
        </div>

        <div v-else :class="message.type">
          <q-chat-message
            avatar="https://cdn.quasar.dev/img/avatar3.jpg"
            :text="[message.text]"
            :stamp="message.date"
            sent
            text-color="white"
            bg-color="primary"
          />
        </div>
      </li>
    </ul>

    <q-card-section class="user-input">
      <q-input
        clearable
        filled
        v-model="text"
        type="text"
        @keyup.enter="sendNewMessage"
        rounded
      >
        <template v-slot:after>
          <q-avatar>
            <q-icon
              name="send"
              background="red"
              size="md"
              color="primary"
              @click="sendNewMessage"
            />
          </q-avatar>
        </template>
      </q-input>
    </q-card-section>
  </div>
</template>

<script>
import moment from "moment";

export default {
  name: "Chat",
  data: () => ({
    text: "",
    messages: [
      {
        type: "document",
        version: 1,
        text: "Titulo del archivo a subir.pdf",
        size: "3.8 MB",
        date: "28 dic. 2018 / 14:45"
      },
      {
        type: "send",
        text:
          "Buenas tardes, acabo de subir el primer archivo con el caso práctico, espero revisión.",
        date: "28 dic. 2018 / 14:45"
      },
      {
        type: "receive",
        text:
          "¡Gran trabajo Silvia! Pero creo que deberías revisar el punto 3. Intenta añadir un poco más de contexto y un apartado final de conclusiones personales.",
        date: "29 dic. 2018 / 10:11"
      },

      {
        type: "document",
        version: 2,
        text: "Titulo del archivo a subir.pdf",
        size: "4.8 MB",
        date: "30 dic. 2018 / 8:22"
      },
      {
        type: "send",
        text: "Realizados los cambios según feedback.",
        date: "30 dic. 2018 / 8:22"
      },
      {
        type: "receive",
        text: "Perfecto, excelente trabajo.",
        date: "30 dic. 2018 / 15:25"
      }
    ]
  }),

  methods: {
    sendNewMessage() {
      moment.locale("es");
      this.messages.push({
        type: "send",
        text: this.text,
        date: moment().format("DD MMM YYYY [/] HH:mm")
      });
    }
  }
};
</script>

<style scoped lang="scss">
ul {
  padding: 0;
  li {
    padding: 1rem;
    list-style-type: none;
  }
}

.document {
  display: flex;
  justify-content: space-between;
  align-items: center;
  border-top: 1px solid rgba(128, 128, 128, 0.3);
  border-bottom: 1px solid rgba(128, 128, 128, 0.3);
  padding: 1rem;

  .text {
    display: flex;
    flex-direction: column;
  }
}

.user-input {
  padding: 1rem;
  border-top: 1px solid rgba(128, 128, 128, 0.3);
  border-width: 100%;
}

i {
  cursor: pointer;
}
</style>
