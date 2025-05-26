<script>
export default {
  name: 'formulario',
  props: [],

  data() {
    return {
      formData: {
        texto: '',
      },
    };
  },

  computed: {
    codificado() {
      const reemplazos = {
        a: 'u',
        e: 'o',
        i: 'i',
        o: 'e',
        u: 'a',
      };

      return this.formData.texto
        .toLowerCase()
        .split('')
        .map(char => reemplazos[char] || char)
        .join('');
    },

    mayusculas() {
      return this.formData.texto.toUpperCase();
    },

    minusculas() {
      return this.formData.texto.toLowerCase();
    },

    minusculasIntercaladas() {
      return this.formData.texto
        .split('')
        .map((char, index) =>
          index % 2 === 0 ? char.toLowerCase() : char.toUpperCase()
        )
        .join('');
    },

    mayusculasIntercaladas() {
      return this.formData.texto
        .split('')
        .map((char, index) =>
          index % 2 === 0 ? char.toUpperCase() : char.toLowerCase()
        )
        .join('');
    },

    cantidadCaracteres() {
      return this.formData.texto.length;
    },
  },
};
</script>


<template>
  <form @submit.prevent>
    <label for="texto">Ingrese texto a codificar 😎</label>
    <input 
      id="texto"
      type="text"
      v-model="formData.texto"
    />
    <div v-if="formData.texto">
      <p>Cantidad de Caracteres: {{ cantidadCaracteres }}</p>
      <p>1 - Codificado: {{ codificado }}</p>
      <p>2 - Mayúsculas: {{ mayusculas }}</p>
      <p>3 - Minúsculas: {{ minusculas }}</p>
      <p>4 - Mayúsculas/Minusculas: {{ mayusculasIntercaladas }}</p>
      <p>5 - Minúsculas/Mayúsculas:{{ minusculasIntercaladas }}</p>
    </div>
  </form>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>
