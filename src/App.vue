<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <v-toolbar-title>Contacts Book</v-toolbar-title>
    </v-app-bar>

    <v-main>
      <v-tabs v-model="tab" centered>
        <v-tab>Contacts Book</v-tab>
        <v-tab>Add Contact</v-tab>
      </v-tabs>
      <v-tabs-items v-model="tab">
        <v-tab-item>
          <ContactList></ContactList>
        </v-tab-item>
        <v-tab-item>
          <ContactRegistrationForm></ContactRegistrationForm>
        </v-tab-item>
      </v-tabs-items>
    </v-main>
  </v-app>
</template>

<script>


import ContactList from "@/components/contacts-list";
import ContactRegistrationForm from "@/components/contact-registration-form";
export default {
  name: 'App',

  components: {
    ContactRegistrationForm,
    ContactList

  },

  data() {
    return{
      tab: null
    }
  },
};
</script>
