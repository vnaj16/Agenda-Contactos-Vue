<template>
    <v-list>
      <template  v-for="contactItem in contacts">
        <ContactItem v-bind:key="contactItem.id" v-bind:contact-item="contactItem"></ContactItem>
      </template>
    </v-list>
</template>

<script>
import ContactItem from "@/components/contact-item";
export default {
  name: "contact-list",
  components:{
    ContactItem

  },
  props:[
      "contacts"
  ]
}
</script>

<style scoped>

</style>