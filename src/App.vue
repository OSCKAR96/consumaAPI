<template>
  <div>
    <h1>pantalla DEMensajes</h1>
    <div class="row container" v-if="usuarios.length">
      <div class="col-3">
        <Usuario
          :imagenUsuario="usuarios[0].picture.large"
          :nombreUsuario="usuarios[0].name.first"
          :posicion="'left'"
          @enviarMsj="agregarChat"
          @keyup.enter="agregarChat"
        />
      </div>

      <div class="col-6">
        <Chat :mensajes="mensajes" />
      </div>

      <div class="col-3">
        <Usuario
          :imagenUsuario="usuarios[1].picture.large"
          :nombreUsuario="usuarios[1].name.first"
          :posicion="'right'"
          @enviarMsj="agregarChat"
          @keyup.enter="agregarChat"
        />
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Chat from "./components/Chat.vue";
import Usuario from "./components/Usuario.vue";

export default {
  name: "App",
  components: {
    Chat,
    Usuario,
  },

  data() {
    return {
      usuarios: [],
      mensajes: [],
    };
  },
  methods: {
    agregarChat: function (nuevoMsj) {
      this.mensajes.push(nuevoMsj);
      console.log(this.mensajes);
    },
  },
  async mounted() {
    try {
      const url = await axios.get("https://randomuser.me/api/?results=2");
      const { data } = url;
      this.usuarios = data.results
    } catch (err) {
      console.error("error en la api: ", err);
    }
  },
};
</script>

<style scoped></style>
