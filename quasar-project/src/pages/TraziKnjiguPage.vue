<template>
  <q-page>
    <div class="q-pa-md">
      <q-card flat bordered>
        <q-card-section>
          <div class="text-h4 text-primary text-center q-mb-md">Pretraživanje</div>
          <p class="text-body1 text-center">
            Pretražite bazu knjiga po naslovu ili autoru.
          </p>
        </q-card-section>
        
        <q-card-section>
          <!-- Pretraga inputa -->
          <q-input
            v-model="searchQuery"
            label="Unesite pojam za pretraživanje"
            :debounce="300"
          />
          <q-checkbox v-model="searchByAuthor" label="Pretraži po autoru" />
          <q-checkbox v-model="searchByTitle" label="Pretraži po naslovu" />
          <q-btn color="primary" label="Traži" @click="searchBooks" />
        </q-card-section>

        <q-card-section>
          <q-table
            :rows="foundBooks"
            :columns="columns"
            row-key="id"
            bordered
            flat
          />
        </q-card-section>
      </q-card>
    </div>
  </q-page>
</template>

<script>
import { ref } from "vue";

export default {
  setup() {
    const searchQuery = ref("");
    const searchByAuthor = ref(false);
    const searchByTitle = ref(false);
    const foundBooks = ref([]);
    
    const books = [
      { id: 1, naslov: "The Picture of Dorian Gray", autor: "Oscar Wilde", opis: "Opis prve knjige.", stanje: "10/10" },
      { id: 2, naslov: "Crime and Punishment", autor: "Fyodor Dostoevsky", opis: "Opis druge knjige.", stanje: "10/10" },
      
    ];

    const columns = [
      { name: "id", label: "ID", align: "left", field: "id" },
      { name: "naslov", label: "Naslov", align: "left", field: "naslov" },
      { name: "autor", label: "Autor", align: "left", field: "autor" },
      { name: "opis", label: "Opis", align: "left", field: "opis" },
      { name: "stanje", label: "Stanje", align: "left", field: "stanje" },
    ];

    function searchBooks() {
      foundBooks.value = books.filter((book) =>
        (searchByAuthor.value && book.autor.toLowerCase().includes(searchQuery.value.toLowerCase())) ||
        (searchByTitle.value && book.naslov.toLowerCase().includes(searchQuery.value.toLowerCase()))
      );
    }

    foundBooks.value = books;

    return { searchQuery, searchByAuthor, searchByTitle, foundBooks, columns, searchBooks };
  },
};
</script>

<style scoped>
.q-card {
  margin-top: 20px;
  background-color: #fff;
}

.q-page {
  background-color: #f4f4f4;
  color: #333;
}
</style>
