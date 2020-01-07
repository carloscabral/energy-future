<template>
  <Layout>
        <div class="top-title">
            <g-image alt="Logo Energy Future" v-if="$page.author.title === 'Energy Future'" src="@/assets/images/img-logo-ef.svg" width="150" />
            <g-image alt="Logo Enel" v-if="$page.author.title === 'Enel'" src="@/assets/images/img-logo-enel.svg" width="150" />
            <g-image alt="Logo Light" v-if="$page.author.title === 'Light'" src="@/assets/images/img-logo-light.svg" width="150" />
            <g-image alt="Logo Energisa" v-if="$page.author.title === 'Energisa'" src="@/assets/images/img-logo-energisa.svg" width="150" />
            <g-image alt="Logo Equatorial" v-if="$page.author.title === 'Equatorial'" src="@/assets/images/img-logo-equatorial.png" width="150" />
            <g-image alt="Logo Santo Antônio" v-if="$page.author.title === 'Santo Antônio'" src="@/assets/images/img-logo-antonio.svg" width="150" />
            <g-image alt="Logo AES Tietê" v-if="$page.author.title === 'AES Tietê'" src="@/assets/images/img-logo-aes.svg" width="150" />
            <h3>Conteúdo exclusivo</h3>
        </div>

        <section id="search-post">
            <div class="row">
                <div class="col-12">
                    <div class="post-search">
                        <label for="search" class="sr-only">Buscar</label>
                        <div class="icon"><font-awesome :icon="['fas', 'search']"/></div>
                        <input type="text" name="search" id="search" placeholder="Pesquisar" v-model="search">
                    </div>
                </div>
            </div>
        </section>

        <div v-if="filteredList.length > 0">
            <div class="row">  
                <article class="col-lg-4 col-md-6 mb-5" v-for="post in filteredList" :key="post.node.id">
                    <g-link :to="post.node.path"><g-image :alt="'Imagem do post ' + post.node.title" class="tag__image" :src="post.node.featured_image" /></g-link>
                    <g-link :to="post.node.path"><p class="tag__title">{{ post.node.title }}</p></g-link>
                    <span class="tag__date">
                        <font-awesome :icon="['fas', 'clock']"/>&nbsp;&nbsp;{{ post.node.date }}
                    </span>     
                </article>
            </div>
        </div> 
        <div v-else>
            <div class="row">
                <div class="col-12 text-center empty">
                    <font-awesome :icon="['fas', 'sad-tear']"/>
                    <p>Sua busca não retornou resultados com as palavras digitadas. Tente novamente!</p>
                </div>
            </div>
        </div>

 </Layout>
</template>

<page-query>
query($id: ID!){
    author(id: $id) {
        title
        belongsTo {
            edges {
            node {
                ... on Post {
                    id
                    title
                    date (format: "DD/MM/YYYY", locale: "pt-BR")
                    author {
                        id
                        path
                    }
                    path
                    featured_image (quality: 80, blur: 0)
                }
            }
            }
        }
    }
}
</page-query>

<script>
export default {
    data: () => ({
        search: ''
    }), 
    
    computed: {
        filteredList() {
            return this.$page.author.belongsTo.edges.filter(post => {
                return post.node.title.toLowerCase().includes(this.search.toLowerCase().trim())
            })
        }
    },    
}
</script>


<style lang="scss">

.top-title {
    display: flex;
    align-items: flex-end;
    flex-wrap: wrap;
    margin: 4.5rem 0 1.5rem 0;

    img {
        margin-right: 1.5rem;
    }

    h3 {
        color: $accent-color-2;
        line-height: .75;
    }
}

</style>
