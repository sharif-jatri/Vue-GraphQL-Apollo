<template>
  <div class="container">
    <div class="row mt-1">
      <table class="table table-bordered">
        <thead>
        <tr>
          <th scope="col">Id</th>
          <th scope="col">Title</th>
        </tr>
        </thead>
        <tbody>
        <tr v-for="item in posts.data" :key="item">
          <td>{{ item.id }}</td>
          <td>{{ item.title }}</td>
        </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>
<script>
import gql from "graphql-tag";
export default {
  name: 'HomeComp',
  apollo: {
    posts: {
      query: gql`
        query (
          $options: PageQueryOptions
        ) {
          posts(options: $options) {
            data {
              id
              title
            }
          }
        }
      `
    },

  },
  data() {
    return {
      posts: []
    };
  }
};
</script>