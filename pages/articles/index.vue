<template>
  <div>
    <div class="d-flex justify-content-between align-items-center">
      <h1>Objets</h1>
      <nuxt-link to="/articles/add" class="btn btn-success"
        >Ajouter un objet</nuxt-link
      >
    </div>

    <div class="alert alert-success" v-if="$route.params.created == 'yes'">
      Record added successfully
    </div>
    <div class="alert alert-success" v-if="$route.params.deleted == 'yes'">
      Record deleted successfully
    </div>

    <table class="table table-hover">
      <tr>
        <th scope="col">Type</th>
        <th scope="col">Nom</th>
        <th scope="col">Details</th>
      </tr>
      <tbody>
        <tr v-for="article in articles" :key="article._id">
          <td>{{ article.title }}</td>
          <td>{{ article.author }}</td>
          <td>{{ article.body }}</td>
          <td>
            <nuxt-link
              class="btn btn-info btn-sm"
              :to="'/articles/' + article._id"
              >Voir
            </nuxt-link>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  async asyncData(context) {
    const { data } = await context.$axios.get('/api/articles')
    return {
      articles: data,
    }
  },
}
</script>
