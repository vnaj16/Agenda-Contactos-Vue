<template>
  <v-card>
    <v-card-title>
      Registration of Contact
    </v-card-title>
    <v-card-text>
      <v-form v-model="isValid" @submit="addContact">
        <v-text-field label="Name"
                      v-model="name"
                      :rules="nameRules"
                      error-count="2"
                      required>
        </v-text-field>
        <v-text-field label="Phone Number"
                      v-model="phoneNumber"
                      :rules="phoneNumberRules"
                      error-count="2"
                      required>
        </v-text-field>
        <v-text-field label="Email"
                      v-model="email"
                      :rules="emailRules"
                      error-count="2"
                      required>
        </v-text-field>
        <v-text-field label="Photo Url"
                      v-model="photoUrl"
                      required>
        </v-text-field>
        <v-card-actions>
          <v-btn color="primary" type="submit" :disabled="!isValid">Add</v-btn>
        </v-card-actions>
      </v-form>
    </v-card-text>

  </v-card>
</template>

<script>
import { v4 as uuidv4 } from 'uuid';
export default {
  name: "contact-registration-form",
  data(){
    return {
      name: null,
      phoneNumber: null,
      email: null,
      photoUrl: null,
      isValid: true,
      nameRules:[
          v => !!v || 'Name is required',
          v => (v && v.length >=2) || 'Name must have at leats 2 characters',
      ],
      phoneNumberRules:[
        v => !!v || 'Phone number is required',
        v => (v && v.length >=7) || 'Phone number must have at leats 7 characters',
      ],
      emailRules:[
        v => !!v || 'Email is required',
        v => /.+@.+/.test(v) || 'Email must be valid'
      ]
      /*
      passwordRules:[
        v => !!v || 'Password is required',
        v => (v && v.length >=5) || 'Password must have at leats 5 characters',
        v => /(?=.*[A-Z])/.test(v) || 'Password must have one uppercase character',
        v => /(?=.*\d)/.test(v) || 'Must have al least one number',
        v => /([!@#$%])/.test(v) || 'Must have al least one special character [!@#$%]'
      ]*/
    }
  },
  methods:{
    addContact(e){
      e.preventDefault();

      const newContactItem = {
        id: uuidv4(),
        name: this.name,
        phoneNumber: this.phoneNumber,
        email: this.email,
        photoUrl: this.photoUrl
      }
      console.log(newContactItem);
      this.$emit('add-contact', newContactItem);
      this.name ='';
      this.phoneNumber = '';
      this.email = '';
      this.photoUrl =''
    }
  }
}
</script>

<style scoped>

</style>