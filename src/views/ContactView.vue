<template>
  <v-form
    name="contact-me"
    @submit.prevent="submit"
    data-netlify="true"
    data-netlify-honeypot="bot-field"
  >
    <p class="hidden">
      <label>
        Don't fill this out if you're human: <input name="bot-field" />
      </label>
    </p>
    <v-container>
      <v-row>
        <v-col cols="12" md="4">
          <v-text-field
            name="name"
            v-model="state.name"
            :error-messages="
              vuelidate.name.$errors.map((e) => e.$message).toString()
            "
            label="Name"
            required
            @input="vuelidate.name.$touch"
            @blur="vuelidate.name.$touch"
          ></v-text-field>
        </v-col>
        <v-col cols="12" md="4">
          <v-text-field
            name="email"
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
            name="message"
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
import axios from "axios";
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

function encode(data: { [key: string]: string }) {
  return Object.keys(data)
    .map(
      (key, value) => `${encodeURIComponent(key)}=${encodeURIComponent(value)}`
    )
    .join("&");
}

function submit() {
  vuelidate.value.$touch();
  if (!vuelidate.value.$error) {
    const config = {
      headers: { "Content-Type": "application/x-www-form-urlencoded" },
    };
    axios.post(
      "/",
      encode({ "form-name": "contact-me", ...state.value }),
      config
    );
    clear();
  }
}
</script>

<style scoped>
.hidden {
  display: none;
  opacity: 0;
}
</style>
