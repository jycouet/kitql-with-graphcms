<script lang="ts" context="module">
  import {
    AllPostsQuery,
    AllPostsQueryStore,
  } from '$lib/graphql/_kitql/graphqlStores'

  export const load = async ({ fetch }) => {
    await AllPostsQuery({ fetch })
    return {}
  }
</script>

<script lang="ts">
  let posts = $AllPostsQueryStore?.data?.posts
</script>

<h1>Welcome to KitQL</h1>

<ul>
  {#each posts ?? [] as { title, excerpt, slug }}
    <li>
      <a class="nice" href={`/posts/${slug}`}>
        <h3>{title}</h3>
        <div class="subtitle">{excerpt}</div>
      </a>
    </li>
  {/each}
</ul>

<style>
  li {
    margin-bottom: 1rem;
  }

  a {
    text-decoration: none;
  }

  h3 {
    margin: 0;
  }
  .subtitle {
    margin-left: 1rem;
    color: darkgrey;
  }
</style>
