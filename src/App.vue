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
          <ContactList v-bind:contacts="contacts"></ContactList>
        </v-tab-item>
        <v-tab-item>
          <ContactRegistrationForm v-on:add-contact="addContact"></ContactRegistrationForm>
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
      tab: null,
      contacts:[
        {
          id:1,
          name: 'Arthur Valladares',
          phoneNumber: '987486321',
          email: 'abc@live.com',
          photoUrl: 'https://cdn.vuetifyjs.com/images/cards/road.jpg'
        },
        {
          id:2,
          name: 'Javier Valladares',
          phoneNumber: '984124321',
          email: 'ert@live.com',
          photoUrl: 'https://cdn.vuetifyjs.com/images/cards/sunshine.jpg'
        },
        {
          id:3,
          name: 'Arthur Nole',
          phoneNumber: '948354321',
          email: 'gfc@live.com',
          photoUrl: 'https://cdn.vuetifyjs.com/images/cards/plane.jpg'
        },
        {
          id:4,
          name: 'Javier Nole',
          phoneNumber: '987654121',
          email: 'yhg@live.com',
          photoUrl: 'https://cdn.vuetifyjs.com/images/cards/house.jpg'
        }
      ]
    }
  },
  methods:{
    addContact(newContact){
      console.log('Hola');
      this.contacts = [...this.contacts, newContact];
    }
  }
};
</script>
