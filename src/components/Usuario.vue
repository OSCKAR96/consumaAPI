<script>
export default {
  name: "Usuario",
  props: {
    imagenUsuario: String,
    nombreUsuario: String,
    posicion: String,
  },
  data() {
    return {
      colorChat: "#fff000",
      textoChat: "",
    };
  },

  methods: {
    enviarMsj: function () {
      const mensajeChat = {
        autor: this.nombreUsuario,
        color: this.colorChat,
        texto: this.textoChat,
        posicion: this.posicion,
      };
      if(this.textoChat.length > 0){
        this.$emit("enviarMsj", mensajeChat)
      }
      this.textoChat ="";
    },
  },
};
</script>

<template>
  <div>
    <div>
        <div>
            <img :src="imagenUsuario" :alt="nombreUsuario">
        </div>

        <div>
            <label><p>{{ nombreUsuario }}</p></label>
        </div>
        <form @submit.prevent="enviarMsj">
            <div>
                <label></label>
                <input type="color" v-model="colorChat">
            </div>
            <div>
                <label for=""></label>
                <textarea v-model="textoChat" @keyup.enter="enviarMsj" id=""></textarea>
            </div>
            <div>
                <button>enviar</button>
            </div>
        </form>
        
    </div>
  </div>
</template>

<style scoped></style>
