<template>
  <q-page>
    <div class="q-pa-md">
      <q-card flat bordered>
        <q-card-section>
          <div class="text-h4 text-primary text-center q-mb-md">Popis svih knjiga</div>
          <p class="text-body1 text-center">
            Ovdje možete vidjeti popis svih dostupnih knjiga u našoj knjižnici.
          </p>
        </q-card-section>
        <q-card-section>
          <q-table
            :rows="books"
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
export default {
  setup() {
    const books = [
      { id: 1, naslov: "The Picture of Dorian Gray ", autor: "Oscar Wilde", opis: "Opis prve knjige.", stanje: "10/10" },
      { id: 2, naslov: "Crime and Punishment", autor: "Fyodor Dostoevsky  ", opis: "Opis druge knjige.", stanje: "10/10" },
    ];

    const columns = [
      { name: "id", label: "ID", align: "left", field: "id" },
      { name: "naslov", label: "Naslov", align: "left", field: "naslov" },
      { name: "autor", label: "Autor", align: "left", field: "autor" },
      { name: "opis", label: "Opis", align: "left", field: "opis" },
      { name: "stanje", label: "Stanje", align: "left", field: "stanje" },
    ];

    return { books, columns };
  },
};
</script>
