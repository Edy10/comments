<template>
  <v-app>
    <v-app-bar app color="primary" dark> </v-app-bar>
    <v-main>
      <Form> </Form>
    </v-main>
  </v-app>
</template>

<script>
  import Form from "./components/Form";
export default {
  name: 'App',

  components: {
    Form
  }
};
</script>
