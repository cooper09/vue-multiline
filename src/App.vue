<template>
  <v-app>
    <v-app-bar app>
      <v-toolbar-title class="headline text-uppercase">
        <span class="font-weight-light">Multi-Line Insurance Agency</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn
        text
        href="http://www.multilineins.com/"
        target="_blank"
      >
        <span class="mr-2">Go to Website</span>
      </v-btn>
    </v-app-bar>

    <v-content>
      <HelloWorld/>
    </v-content>
  </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld';

export default {
  name: 'App',
  components: {
    HelloWorld,
  },
  data: () => ({
    //
  }),
};
</script>
