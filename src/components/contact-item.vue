<template>
  <v-card>
    <v-img :src="contactItem.photoUrl" height="200"></v-img>
    <v-card-title>{{contactItem.name}}</v-card-title>
    <v-card-subtitle>
      {{contactItem.phoneNumber}}
    </v-card-subtitle>
    <v-card-actions>
      <v-btn
          color="orange lighten-2"
          text
      >
        Explore
      </v-btn>

      <v-spacer></v-spacer>

      <v-btn
          icon
          @click="show = !show"
      >
        <v-icon>{{ show ? 'mdi-chevron-up' : 'mdi-chevron-down' }}</v-icon>
      </v-btn>
    </v-card-actions>

    <v-expand-transition>
      <div v-show="show">
        <v-divider></v-divider>

        <v-card-text>
          Email: {{contactItem.email}}
        </v-card-text>
      </div>
    </v-expand-transition>
  </v-card>
</template>

<script>
export default {
  name: "contact-item",
  data(){
    return{
      show:false
    }
  },
  components:{

  },
  props:[
    "contactItem"
  ]
}
</script>

<style scoped>

</style>