<template>
    <Layout>
        <article class="single-post">
            <div class="row">
                <div class="col-md-10 offset-md-1">
                    <h1 class="single-post__title">{{ $page.post.title }}</h1>
                    <small class="single-post__credits">Por: <g-link :to="$page.post.author.path">{{ $page.post.author.id }}</g-link>&nbsp;&nbsp;|&nbsp;&nbsp;<font-awesome class="single-post__icon" :icon="['fas', 'clock']"/>&nbsp;&nbsp;{{ $page.post.date }}</small>
                </div>
            </div>
            <div class="row mt-4">
                <div class="col-md-10 offset-md-1"><g-image class="single-post__image" :alt="'Imagem do post ' + $page.post.author.title" :src="$page.post.featured_image" /></div>
            </div>
            <div class="row mt-3">
                <p class="col-md-10 offset-md-1 single-post__excerpt" v-html="$page.post.excerpt"></p>
            </div>
            <div class="row single-post__content">
                <div class="col-md-10 offset-md-1 mb-5 share">
                    <SocialShare :hasRotation="false" :url="'https://www.energyfuture.com.br'+ $page.post.path" />
                </div>
                <div class="col-md-10 offset-md-1 col-md-10 offset-md-1">
                    <p align="justify" v-html="$page.post.content"></p>
                    <p class="single-post__tag-title">tags:</p>
                    <div class="single-post__tag-list">
                        <g-link v-for="tag in $page.post.tags" :to="tag.path" :key="tag.id">{{ tag.id }}</g-link>
                    </div>
                    <vue-disqus shortname="energy-future-1" :identifier="$page.post.title"></vue-disqus>
                </div>              
            </div>
        </article>

    </Layout>    
</template>

<page-query>
query($path: String!){
        post(path: $path) {
            title
            date (format: "DD/MM/YYYY", locale: "pt-BR")
            excerpt
            content
            path
            tags {
                id
                path
            }
            author {
                id
                path
            }            
            featured_image (quality: 80, blur: 0)
    }
}
</page-query>

<script>
import SocialShare from '~/components/SocialShare.vue'

export default {
    metaInfo() {
        return {
            title: this.$page.post.title,
            meta: [
                {
                    key: 'og:description',
                    name: 'og:description',
                    content: this.$page.post.description,
                },

                {
                    key: 'twitter:description',
                    name: 'twitter:description',
                    content: this.$page.post.description,
                },
            ],
        }
    },
    components: { SocialShare }
}
</script>
</script>


<style lang="scss">

.single-post {

    strong {
        color: $accent-color-2;
    }

    p {
        hyphens: auto;
        text-rendering:  optimizeLegibility;
    }

    h2 {
        margin: 3rem 0 1.5rem 0;
        color: $primary-color;
        font-weight: 600;
        letter-spacing: -.5px;
    }

    &__title {
        @extend .main-title;
        margin-bottom: 1.5rem;
        //max-width: 42rem;
    }

    &__credits {
        text-transform: uppercase;
        font-size: .77rem;
        letter-spacing: .7px;
        font-weight: 700;
        color: $text-color;

        a {
            color: $accent-color-2;
            font-size: inherit;

            &:hover {
                color: $primary-color;
            }
        }
    }

    &__icon {
        color: $accent-color-1;
    }
    
    &__excerpt {
        margin-top: 1.5rem;
        font-size: 1rem;
        font-style: italic;
        color: $primary-color;
        font-weight: 500;
        @media(min-width: 768px) {
            margin-top: 0;
        }
        @media(min-width: 992px) {
            font-size: 1.35rem;
        }        
    }

    &__image {
        width: 100%;
        height: auto;
    }

    &__content {
        margin-top: 3rem;
        // @media(min-width: 992px) {
        //     margin-top: 5rem;
        // }

        img {
            width: 100%;
            margin: 1.5rem 0;
            box-shadow: 0 2rem 5rem rgba($primary-color, 0.12);
            @media (min-width: 1200px) {
                width: 115%;
            }
        }
        
        blockquote p {
            color: $primary-color;
            font-style: italic;
            font-weight: 500;
            font-size: 1rem !important;
            text-indent: -.4rem;

            @media(min-width: 768px) {
                font-size: 1rem !important;
                float: right;
                max-width: 20rem;
                padding: 0 3rem;
            }
        }
    }

    &__tag-title {
        text-transform: uppercase; 
        color: $primary-color;
        letter-spacing: .7px; 
        font-size: .77rem; 
        font-weight: 600; 
        margin-top: 3rem;
        margin-bottom: 0; 
    }

    &__tag-list {

        display: flex;
        flex-wrap: wrap;
        margin-bottom: 1.5rem;

        a {
            background-color: rgba($accent-color-2, .1);
            letter-spacing: .7px;
            color: $accent-color-2;
            margin: .5rem 0;
            padding: .35rem .5rem;
            font-size: .66rem;
            text-transform: uppercase;

            &:hover {
                background-color: $accent-color-2;
                color: #fff;
            }
        }

        a:not(:last-child) {
            margin-right: 1rem;            
        }
    }     
   
}

</style>

