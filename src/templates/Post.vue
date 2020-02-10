<template>
  <Layout>
    <div class="post-title">
      <h1 class="post-title__text">
        {{ $page.post.title }}
      </h1>

      <PostMeta :post="$page.post" />

    </div>

    <div class="post content-box">
      <div class="post__header">
        <g-image alt="Cover image" v-if="$page.post.cover_image" :src="$page.post.cover_image" />
      </div>

      <div class="post__content" v-html="$page.post.content" />

      <div class="post__footer">
        <PostTags :post="$page.post" />
      </div>
    </div>

    <div class="post-comments">
      <!-- Add comment widgets here -->
    </div>

    <Author class="post-author" />
  </Layout>
</template>

<script>
import PostMeta from '~/components/PostMeta'
import PostTags from '~/components/PostTags'
import Author from '~/components/Author.vue'

export default {
  components: {
    Author,
    PostMeta,
    PostTags
  },
  metaInfo () {
    return {
      title: this.$page.post.title,
      meta: [
        {
          name: 'description',
          content: this.$page.post.description
        },
        {
          name: 'robots',
          content: "follow,index,max-snippet:-1,max-video-preview:-1,max-image-preview:large"
        },
        {
          property: "og:locale",
          content:"en_GB"
        },
         {
          name: 'og:type',
          content:  this.$page.post.title
        },
         {
          property: "og:type",
          content:"article"
        },
        {
          property: "og:description",
          content: this.$page.post.description
        },
          {
          property: "og:url",
          content: window.location.href
        },
          {
          property: "article:author",
          content: "http://facebook.com/manascodes/"
        },
        {
          property: "article:tag",
          content: this.$page.post.tag
        },
        {
          property: "og:updated_time",
          content: this.$page.post.date
        },
          {
          property: "og:image",
          content: this.$page.post.cover_image
        },
        
        {
          property: "og:image:secure_url",
          content: this.$page.post.cover_image
        },
        {
          property: "og:image:width",
          content: "600"
        },
         {
          property: "og:image:height",
          content: "600"
        },
        {
          property: "og:image:alt",
          content: this.$page.post.title
        },
         {
          property: "og:image:type",
          content: "image/jpg"
        },
        {
          name: "twitter:card",
          content:"summary_large_image"
        },
        {
          name: "twitter:title",
          content: this.$page.post.title
        },
         {
          name: "twitter:description",
          content: this.$page.post.description
        },
        {
          name: "twitter:creator",
          content: '@man_as_code'
        },
        {
          name: "twitter:image",
          content: this.$page.post.cover_image
        },
      ],
      link: [
      { rel: 'canonical', href: window.location.href },
      ]
    }
  },
  created(){
    // console.log(window.location.href);
  }
}
</script>

<page-query>
query Post ($id: ID!) {
  post: post (id: $id) {
    title
    path
    date (format: "D. MMMM YYYY")
    timeToRead
    tags {
      id
      title
      path
    }
    description
    content
    cover_image (width: 860, blur: 10)
  }
}
</page-query>

<style lang="scss">
.post-title {
  padding: calc(var(--space) / 2) 0 calc(var(--space) / 2);
  text-align: center;
}

.post {

  &__header {
    width: calc(100% + var(--space) * 2);
    margin-left: calc(var(--space) * -1);
    margin-top: calc(var(--space) * -1);
    margin-bottom: calc(var(--space) / 2);
    overflow: hidden;
    border-radius: var(--radius) var(--radius) 0 0;

    img {
      width: 100%;
    }

    &:empty {
      display: none;
    }
  }

  &__content {
    h2:first-child {
      margin-top: 0;
    }

    p:first-of-type {
      font-size: 1.2em;
      color: var(--title-color);
    }

    img {
      width: calc(100% + var(--space) * 2);
      margin-left: calc(var(--space) * -1);
      display: block;
      max-width: none;
    }
  }
}

.post-comments {
  padding: calc(var(--space) / 2);

  &:empty {
    display: none;
  }
}

.post-author {
  margin-top: calc(var(--space) / 2);
}
</style>
