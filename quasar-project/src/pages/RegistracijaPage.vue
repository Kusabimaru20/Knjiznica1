<template>
  <q-page>
    <div class="q-pa-md">
      <q-card flat bordered>
        <q-card-section>
          <div class="text-h4 text-primary text-center">Registracija korisnika</div>
          <p class="text-body1 text-center">
            Ispunite potrebna polja za registraciju.
          </p>
        </q-card-section>
        <q-card-section>
          <q-input v-model="user.ime" label="Ime" outlined class="q-mb-md" />
          <q-input v-model="user.prezime" label="Prezime" outlined class="q-mb-md" />
          <q-input v-model="user.email" label="Email" type="email" outlined class="q-mb-md" />
          <q-input v-model="user.lozinka" label="Lozinka" type="password" outlined class="q-mb-md" />
          <q-btn color="primary" label="Registriraj se" @click="registerUser" />
        </q-card-section>
      </q-card>
    </div>
  </q-page>
</template>

<script>
import { ref } from "vue";

export default {
  setup() {
    const user = ref({
      ime: "",
      prezime: "",
      email: "",
      lozinka: "",
    });

    function registerUser() {
      console.log("Registrirani korisnik:", user.value);
    }

    return { user, registerUser };
  },
};
</script>