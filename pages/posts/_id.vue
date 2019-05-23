<template>
    <div class="container">
        <article>
            <h1>{{selected_post.id}}</h1>
            <p>Google Chrome is a free, open-source web browser developed by Google, released in 2008.</p>
        </article>
        <aside>
            <h3>post you might enjoy </h3>
            <ul>
                <li v-for="related in related_posts" v-bind:key="related.id">
                    <nuxt-link :to="`/posts/${related.id}`">{{related.id}}</nuxt-link>
                </li>
            </ul>
        </aside>
    </div>
</template>


<script>
export default {
    head()
{
  return{
    title: 'Post'+' '+this.selected_post.id,
    meta:[
        {name:'twitter:title',content:this.selected_post.id},
        {name:'twitter:description',content:this.selected_post.content},
        {name:'twitter:image',content:'https://picsum.photos/id/10/1024/480'},
        {name:'twitter:card',content:'summary largee_imaggge'},
        
    ]
  }

},
    data(){
    return{
        id:this.$route.params.id,
        // posts:[
        //   {
        //     id:'Worker',
        //     content:'hello'
        //   },
        //   {
        //     id:'Observable',
        //     content:'locks'
        //   }
        // ]
    }
  },
  computed:{
    selected_post()
    {
      return this.$store.state.posts.all.find(post=>post.id==this.id)
    },
    related_posts()
    {
        return this.$store.state.posts.all.filter(post=>post!=this.id)
    }
  }
}
</script>


<style>

</style>


