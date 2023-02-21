<template>
  <v-table>
    <thead>
      <tr>
        <th class="text-left">
          Autor
        </th>
        <th class="text-left">
          Titulo
        </th>
        <th class="text-left">
          Post
        </th>
      </tr>
    </thead>
    <tbody class="text-h6 text-md-h5 text-lg-h5">
      <tr
        v-for="item in titles"
        :key="item.titles"
      >
        <td>{{ autores[item.userId-1].name }}</td>
        <td>{{ item.title }}</td>
        <td>{{ item.body }}</td>
      </tr>
    </tbody>
  </v-table>
</template>

<script>
const titles = []
const autores = []
fetch('https://jsonplaceholder.typicode.com/posts')
  .then((response) => response.json())
  .then((json) => {
  for (let i =0; i< json.length ;i++) {
   titles.push(json[i])
  }
  });

fetch('https://jsonplaceholder.typicode.com/users')
  .then((response) => response.json())
  .then((json) => {
  for (let i =0; i< json.length ;i++) {
   autores.push(json[i])
  }
  });



  export default {
    data () {
      return {
        titles, autores,
      }
    },
  }
</script>