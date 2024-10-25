<script>
export default {
  name: "Chat",
  props: {
    mensajes: Array,
  },
};
</script>

<template>
  <div>
    <div
      v-for="(mensaje, index) in mensajes"
      :key="index"
      :style="{ textAlign: mensaje.posicion }"
    >
      <div>
        <span>{{ mensaje.autor }}</span>
        <div>
          <span
            :style="{
              backgroundColor: mensaje.color,
              textAlign: mensaje.posicion,
            }"
          >
            {{ mensaje.texto }}
          </span>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped></style>
