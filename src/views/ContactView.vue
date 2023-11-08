<template>
  <v-form @submit.prevent="submit" data-netlify="true">
    <v-container>
      <v-row>
        <v-col cols="12" md="4">
          <v-text-field
            v-model="state.name"
            :error-messages="
              vuelidate.name.$errors.map((e) => e.$message).toString()
            "
            label="First name"
            required
            @input="vuelidate.name.$touch"
            @blur="vuelidate.name.$touch"
          ></v-text-field>
        </v-col>
        <v-col cols="12" md="4">
          <v-text-field
            v-model="state.email"
            :error-messages="
              vuelidate.email.$errors.map((e) => e.$message).toString()
            "
            label="E-mail"
            required
            @input="vuelidate.email.$touch"
            @blur="vuelidate.email.$touch"
          ></v-text-field>
        </v-col>
        <v-col cols="12" md="8">
          <v-textarea
            v-model="state.message"
            :error-messages="
              vuelidate.message.$errors.map((e) => e.$message).toString()
            "
            label="Message"
            required
            @input="vuelidate.message.$touch"
            @blur="vuelidate.message.$touch"
          ></v-textarea>
        </v-col>
      </v-row>
      <v-row>
        <v-col cols="12" md="2">
          <v-btn type="submit" block class="mt-2">Submit</v-btn>
        </v-col>
      </v-row>
    </v-container>
  </v-form>
</template>

<script setup lang="ts">
import { ref } from "vue";
import { useVuelidate } from "@vuelidate/core";
import { email, required } from "@vuelidate/validators";

const initialValues = {
  name: "",
  email: "",
  message: "",
};

const state = ref(initialValues);

const rules = {
  name: { required },
  email: { required, email },
  message: { required },
};

const vuelidate = useVuelidate(rules, state);

function clear() {
  vuelidate.value.$reset();
  state.value = {
    name: "",
    email: "",
    message: "",
  };
}

function submit() {
  vuelidate.value.$touch();
  if (!vuelidate.value.$error) {
    let obj = {
      name: state.value.name,
      email: state.value.email,
      message: state.value.message,
    };
    console.log(obj);
    clear();
  }
}

// function handleSubmit(event: Event) {
//   const form = event.target as HTMLFormElement;
//   const formData = new FormData(form);
//   let obj: ContactForm = {
//     name: name.value,
//     email: email.value,
//     message: formData.get("message") as string,
//   };

//   console.log(obj);

// fetch("/", {
//   method: "POST",
//   headers: { "Content-Type": "application/x-www-form-urlencoded" },
//   body: new URLSearchParams(JSON.stringify(obj)).toString(),
// });
// }
</script>

<style scoped></style>
