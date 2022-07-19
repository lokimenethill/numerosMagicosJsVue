<template>
  <v-row justify="center" align="center">
    <v-col >
      <v-card>
        <cuadro-magico></cuadro-magico>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
import cuadroMagico from '../components/cuadroMagico.vue'
export default {
  components: { cuadroMagico },
  name: 'IndexPage'
}
</script>
