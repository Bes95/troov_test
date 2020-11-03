<template>
  <div>
    <h1>Details Objet</h1>

    <div class="alert alert-success" v-if="$route.params.updated == 'yes'">
      Record updated successfully
    </div>

    <table class="table table-hover">
      <tr>
        <th scope="col">Type</th>
        <th scope="col">Nom</th>
        <th scope="col">Details</th>
      </tr>

      <tbody>
        <tr>
          <td>{{ article.title }}</td>
          <td>{{ article.author }}</td>
          <td>{{ article.body }}</td>
          <td>
            <nuxt-link
              :to="'/articles/' + article._id + '/update'"
              class="btn btn-primary mr-3"
              >Modifier</nuxt-link
            >
            <button
              type="button"
              class="btn btn-danger mr-3"
              @click="deleteRecord()"
            >
              Supprimer
            </button>
          </td>
        </tr>
      </tbody>
    </table>

    <hr />
    <div class="d-flex justify-content-between">
      <nuxt-link to="/articles" class="btn btn-secondary mr-3"
        >Liste des objets</nuxt-link
      >
    </div>
  </div>
</template>

<script>
export default {
  middleware: 'auth',

  async asyncData(context) {
    const { data } = await context.$axios.get(
      '/api/articles/' + context.route.params.id
    )
    return {
      article: data,
    }
  },

  methods: {
    deleteRecord() {
      if (confirm('Are you sure?') === true) {
        this.$axios
          .delete('/api/articles/' + this.$route.params.id)
          .then((response) => {
            if (response.data._id) {
              this.$router.push({
                name: 'articles',
                params: { deleted: 'yes' },
              })
            }
          })
          .catch((error) => {
            console.log(error)
          })
      }
    },
  },
}
</script>
