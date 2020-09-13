<template>
  <table class="table">
      <thead>
          <tr>
              <th scope="col">Nome</th>
              <th scope="col">E-mail</th>
              <th scope="col">Nascimento</th>
              <th scope="col">Serviços</th>
              <th scope="col">Total</th>
          </tr>
      </thead>
      <tbody>
          <tr v-for="(table, indice) in tables" :key="indice">
              <td><span>{{table.nome}}</span></td>
              <td><span>{{table.email}}</span></td>
              <td><span>{{table.nascimento}}</span></td>
              <td><span>{{table.servicos}}</span></td>
              <td><span>{{table.total}}</span></td>
          </tr> 
      </tbody>
  </table>
</template>

<script>
export default {
    name:"Table",
    props:['tables']
}
</script>

<style>

</style>