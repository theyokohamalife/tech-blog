<template>
  <div>
    <h1>Blog Posts</h1>
    <v-container>
      <v-row dense>
        <v-col cols="12" v-for="article of articles" :key="article.slug">
          <v-card elevation="2" dark>
            <NuxtLink :to="{ name: 'blog-slug', params: { slug: article.slug } }" class="text-decoration-none">
              <!-- <img :src="article.img" /> -->
              <v-card-title class="headline font-weight-bold">{{ article.title }}</v-card-title>
              <v-card-subtitle>
                <p>by {{ article.author.name }}</p>
              </v-card-subtitle>
              <v-card-text>
                <p>{{ article.description }}</p>
              </v-card-text>
            </NuxtLink>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>


<script>
export default {
  async asyncData({ $content, params }) {
    const articles = await $content("articles", params.slug)
      .only(["title", "description", "img", "slug", "author"])
      .sortBy("createdAt", "asc")
      .fetch();

    return {
      articles,
    };
  },
};
</script>