<template>
  <v-footer color="transparent" absolute fixed>
    <v-row justify="center" no-gutters>
      <v-btn class="ma-2" x-large color="primary" icon rounded>
        <v-icon>mdi-vuetify</v-icon>
      </v-btn>
      <v-col class="primary lighten-2 py-4 text-center white--text" cols="12">
        {{ new Date().getFullYear() }} ©
        <strong>พัฒนาโดย AloneCoding's Team</strong>
      </v-col>
    </v-row>
  </v-footer>
</template>

<script>
export default {};
</script>

<style>
</style>