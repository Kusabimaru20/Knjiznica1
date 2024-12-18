<template>
  <q-page>
    <div class="q-pa-md">
      <q-card flat bordered>
        <q-card-section>
          <div class="text-h4 text-primary text-center">Prijava korisnika</div>
          <p class="text-body1 text-center">
            Unesite svoje korisničke podatke za prijavu.
          </p>
        </q-card-section>
        <q-card-section>
          <q-input v-model="username" label="E-mail" outlined class="q-mb-md" />
          <q-input v-model="password" label="Lozinka" type="password" outlined class="q-mb-md" />
          <q-btn color="primary" label="Prijavi se" @click="login" />
        </q-card-section>
      </q-card>
    </div>
  </q-page>
</template>

<script>
import { ref } from "vue";

export default {
  setup() {
    const username = ref("");
    const password = ref("");

    function login() {
      console.log("Prijava korisnika:", { username: username.value, password: password.value });
    }

    return { username, password, login };
  },
};
</script>
