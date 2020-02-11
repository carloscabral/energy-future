<template>
  <Newest> 
      <div class="row my-4">
          <g-image alt="Logo Energy Future" src="@/assets/images/img-logo-ef.svg" />
      </div>
      <div class="lp-hero__bg"></div>  
      <div class="row mt-5">
          <div class="col-xl-6 hero">
              <h1 class="lp-hero__title">A maior chamada de projetos de P&D do setor elétrico brasileiro.</h1>
              <h3 class="lp-hero__subtitle">O Energy Future, hub virtual de inovação do setor elétrico, conecta projetos a grandes concessionárias do país. Procuramos soluções inovadoras que ajudem a melhorar a geração, distribuição e transmissão de energia elétrica no Brasil.</h3>
              <g-link to="https://energyfuture.typeform.com/to/QvbsS6" target="_blank"><button class="lp-hero__button">Faça seu cadastro</button></g-link>
          </div>
          <div class="col-xl-6 mt-4 mt-xl-0 lp-hero__video">
              <iframe title="Video de destaque" src="https://player.vimeo.com/video/389214543" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>
          </div>
      </div>
      <div class="row">
          <div class="col-12">
              <h3 class="line-title">As empresas que irão analisar o seu projeto</h3>
          </div>
          <div class="col-12 companies">
              <ul class="companies__list">
                  <li class="companies__item"><g-image alt="Logo AES" src="../assets/images/img-logo-aes.svg" with="100" /></li>
                  <li class="companies__item"><g-image alt="Logo Energisa" src="../assets/images/img-logo-energisa.svg" with="100" /></li>
                  <li class="companies__item"><g-image alt="Logo Equatorial" src="../assets/images/img-logo-equatorial.png" with="100" /></li>
                  <li class="companies__item"><g-image alt="Logo Enel" src="../assets/images/img-logo-enel.svg" with="100" /></li>
                  <li class="companies__item"><g-image alt="Logo Light" src="../assets/images/img-logo-light.svg" with="100" /></li>
                  <li class="companies__item"><g-image alt="Logo Sto. Antonio" src="../assets/images/img-logo-antonio.svg" with="100" /></li>
              </ul>
          </div>
      </div>
      <div class="color-box">
        <div class="row justify-content-lg-between text-center">
            <div class="col-12">
                <h3 class="color-box__title">Quem pode se inscrever no Energy Future?</h3>
            </div>
            <div class="col-lg-2 col-md-4 col-sm-6">
                <g-image alt="Logo Startups" class="color-box__icon" src="../assets/images/new-page/ic-startups.svg" width="100" />
                <p class="color-box__text">Startups</p>
            </div>
            <div class="col-lg-2 col-md-4 col-sm-6">
                <g-image alt="Logo Pesquisadores" class="color-box__icon" src="../assets/images/new-page/ic-pesquisadores.svg" width="100" />
                <p class="color-box__text">Pesquisarores</p>
            </div>
            <div class="col-lg-2 col-md-4 col-sm-6">
                <g-image alt="Logo Corporações" class="color-box__icon" src="../assets/images/new-page/ic-corporacoes.svg" width="100" />
                <p class="color-box__text">Corporações</p>
            </div>
            <div class="col-lg-2 col-md-4 col-sm-6">
                <g-image alt="Logo Pequenas Empresas" class="color-box__icon" src="../assets/images/new-page/ic-pequenas-empresas.svg" width="100" />
                <p class="color-box__text">Pequenas Empresas</p>
            </div>
            <div class="col-lg-2 col-md-4 col-sm-6">
                <g-image alt="Logo Médias Empresas" class="color-box__icon" src="../assets/images/new-page/ic-medias-empresas.svg" width="100" />
                <p class="color-box__text">Médias Empresas</p>
            </div>                        
        </div>
      </div>
      <div class="row mt-3">
        <div class="col-12">
            <h3 class="line-title">Categorias da chamada Energy Future</h3>
            <p class="mt-3 mb-5" style="max-width: 800px;">Entender as atuais necessidades do setor de energia elétrica é o primeiro passo na proposta de um projeto de caráter inovador. Por isso, o Energy Future estabeleceu as principais categorias, diretrizes, para orientar os novos negócios.</p>
            <div v-for="(item, index) in items" :key="index">
                <Collapse :title="item.title" :text="item.text" />
            </div>               
        </div>
      </div> 
      <div class="row mt-3">
        <div class="col-12">
            <h3 class="line-title">Qual a garantia de propriedade intelectual?</h3>
            <p class="mt-3 mb-5" style="max-width: 800px;">A chamada está alinhada aos regulamentos da ANEEL na garantia da Propriedade Intelectual. Os projetos inscritos estão preservados, de acordo com as leis nº 9.279/96 (Propriedade Industrial) e 9.610/98 (Direito Autoral).</p>              
        </div>
      </div>
      <div class="testimonial my-5">
        <div class="row text-center">
            <div class="col-lg-10 offset-lg-1">
                <p class="testimonial__text">{{ testimonials[activeTestimonial].text }}</p>
                <cite class="testimonial__author">{{ testimonials[activeTestimonial].author }}</cite>
            </div>
            <div v-show="activeTestimonial > 0" class="testimonial__button previous" @click="goPrev"><font-awesome :icon="['fas', 'chevron-left']"/></div>
            <div v-show="activeTestimonial < testimonials.length - 1" class="testimonial__button next" @click="goNext"><font-awesome :icon="['fas', 'chevron-right']"/></div>
        </div>
      </div>

      <div id="bottom-cards">
          <div class="row">
              <div class="col-xl-4 col-lg-6 col-md-6 mt-5 px-xl-2">
                  <div class="new-card new-card--1">
                      <h3 class="new-card__icon"><g-image alt="Ícone de regulamento" class="color-box__icon" src="../assets/images/new-page/img-regulamentos.svg" width="75" /></h3>
                      <h4 class="new-card__title">O que preciso saber para a inscrição no Energy Future?</h4>
                      <p class="new-card__divider new-card__divider--1"></p>
                      <g-link to="../assets/images/Regulamento-Energy-Future-Oficial.pdf" target="_blank" class="new-card__link new-card__link--1"><font-awesome :icon="['fas', 'arrow-right']"/>Regulamento Energy Future</g-link>
                      <g-link to="../assets/images/PROP&D.zip" target="_blank" class="new-card__link new-card__link--1"><font-awesome :icon="['fas', 'arrow-right']"/>Regulamento Aneel</g-link>
                  </div>
              </div>
              <div class="col-xl-4 col-lg-6 col-md-6 mt-5 px-xl-2">
                <div class="new-card new-card--2">
                    <h3 class="new-card__icon"><g-image alt="Ícone de prazo de inscrição" class="color-box__icon" src="../assets/images/new-page/img-encerramento.svg" width="75" /></h3>
                    <h4 class="new-card__title">Até quando posso realizar a inscrição?</h4>
                    <p class="new-card__divider new-card__divider--2"></p>
                    <g-link to="/inscricao/" target="_blank" class="new-card__link new-card__link--2">O encerramento das inscrições será no dia <strong>30/01/2020</strong></g-link>
                </div>
              </div>
              <div class="col-xl-4 col-lg-6 col-md-6 mt-5 px-xl-2">
                <div class="new-card new-card--3">
                    <h3 class="new-card__icon"><g-image alt="Ícone de dúvidas" class="color-box__icon" src="../assets/images/new-page/img-faq.svg" width="75" /></h3>
                    <h4 class="new-card__title">Dúvidas? Veja nossas perguntas e respostas mais frequentes:</h4>
                    <p class="new-card__divider new-card__divider--3"></p>
                    <g-link to="/duvidas/" class="new-card__link new-card__link--3"><font-awesome :icon="['fas', 'arrow-right']"/>Acesse nosso FAQ</g-link>
                </div>           
              </div>
          </div>
      </div>

      <div class="call-to-action">
          <div class="row text-center">
              <div class="col-12">
                  <g-link to="https://energyfuture.typeform.com/to/QvbsS6" target="_blank"><button class="cta-btn">Faça seu cadastro</button></g-link>
              </div>
          </div>
      </div>

      <div class="lp-footer">
          <div class="row">
              <h3 class="col-12 text-center mb-4">Apoio</h3>
          </div>
          <div class="row text-center">
              <div class="col-6 col-sm-6 col-md-4 col-lg-3 col-xl-2" v-for="(logo, index) in logoNames" :key="index">
                  <g-image class="lp-supporters" alt="Logo da empresa apoiadora " :src="require(`../assets/images/${logo}`)" width="75"></g-image>
              </div>
          </div>
          <div class="row my-5 align-items-end">
              <div class="my-3 my-lg-0 text-center text-md-left col-lg-3"><g-image alt="Logo Energy Future" class="lp-footer__bottom-logos ef" src="../assets/images/img-logo-ef-light.svg" width="200" /></div>
              <div class="my-3 my-lg-0 text-center text-md-left col-lg-3"><g-image alt="Logo PD Aneel" class="lp-footer__bottom-logos aneel" src="../assets/images/img-logo-pdaneel-light.svg" width="200" /></div>
              <g-link to="/inscricao/" class="my-3 my-lg-0 text-center text-md-left text-lg-right col-lg-6 lp-footer-link">Inscreva seu projeto&nbsp;&nbsp;<font-awesome :icon="['fas', 'arrow-right']"/></g-link>
          </div>
      </div>

  </Newest>
</template>

<script>
import Collapse from '~/components/Collapse.vue'

export default {
  metaInfo: {
    title: 'Inscrição Energy Future',
    meta: [
      { charset: 'utf-8' },
      { name: "author", content: "Carlos Gomes Cabral" },
      { name: "description", content: "O setor elétrico está buscando projetos e startups que possam trazer inovação na geração, transmissão ou distribuição de energia. Inscreva-se!" },
      { name: "keywords", content: "Startups, Inovação, Setor elétrico, Concessionárias de energia" },
      { key: 'og:title', name: 'og:title', content: 'Energy Future - Inscreva-se' },
      { key: 'twitter:title', name: 'twitter:title', content: 'Energy Future - Inscreva-se' }      
    ]
  },    
  data: () => ({
    activeTestimonial: 0,
    items : [
        { title : 'Renováveis e Storage', text: 'Novas fontes renováveis e sustentáveis de energia e maneiras inovadoras de conversão e armazenamento de energia, incluindo novos combustíveis e soluções de integração, instalação, manutenção e gestão dessas tecnologias.' },
        { title : 'Smart Grid and Meter', text: 'Redes inteligentes de energia com nova arquitetura de geração, transmissão e distribuição de eletricidade, mais segura e inteligente, que integre e possibilite ações a todos os usuários a elas conectados. Para as distribuidoras de energia elétrica, a medição inteligente (smart metering) é considerada uma das etapas do Smart Grid.' },
        { title : 'Gestão energética', text: 'Soluções alternativas e integradas, que aperfeiçoem o uso das fontes de energia elétrica para melhorar o consumo e o monitoramento do uso de recursos.' },
        { title : 'Novos Negócios em Geração e Transmissão', text: 'Desenvolvimento de soluções inovadoras ou novas formas de geração e transmissão voltadas para B2G, B2B e B2C.' },
        { title : 'Serviços ao Cliente de Distribuição', text: 'Novos serviços e soluções direcionados para o cliente consumidor de energia elétrica; hardware e Software aplicados à mobilidade elétrica; novas formas de arrecadação das contas de energia: serviços ﬁnanceiros e soluções para clientes não bancarizados.' },
        { title : 'Performance e Digitalização', text: 'Inovação e eﬁciência na geração de produtos e serviços que melhorem o dia a dia do setor de energia; soluções em tecnologia e processos, por meio da conectividade e da troca e envio de dados.' }
    ],
    logoNames: [
        "img-apoio-cesar.svg",
        "img-apoio-open-innovation.svg",
        "img-apoio-abmen.svg",
        "img-apoio-abraceel.svg",
        "img-apoio-firjan.svg",
        "img-apoio-parque.svg",
        "img-apoio-coppe.svg",
        "img-apoio-startupi.svg",
        "img-apoio-fiec.svg",
        "img-apoio-senai.svg",
        "img-apoio-senai4.svg",
        "img-apoio-midas.svg",
        "img-apoio-abradee.svg",
        "img-apoio-anjos.svg",
        "img-apoio-fiep.svg",
        "img-apoio-fiems.svg",
        "img-apoio-senai2.svg",
        "img-apoio-fits.svg",
        "img-apoio-fiepa.svg",
        "img-apoio-fiero.svg",
        "img-apoio-cni.svg",
        "img-apoio-estrategico-abacomm.svg",
        "img-apoio-estrategico-centralcomm.svg",
        "img-apoio-estrategico-acate.svg",
        "img-apoio-estrategico-aqwa.svg",
        "img-apoio-estrategico-ist.svg",        
    ],
    testimonials: [
      { author : 'Sunny Jonathan - Coordenador de P&D&I no IST ENERGIA/SENAI SP', text: '“O IST ENERGIA do SENAI São Paulo apoia o ENERGY FUTURE, pois é uma grande oportunidade para viabilizar projetos com produtos e resultados que agreguem valor aos negócios das concessionárias do setor elétrico, principalmente nas fases finais da cadeia de inovação, onde o IST ENERGIA tem seu foco de atuação.”' },
      { author : 'Julia Rodrigues, coordenadora de P&D e Inovação da AES Tietê', text: '“O Energy Future é uma iniciativa muito importante para o setor, pois comunica ao mercado, incluindo indústrias, centros de pesquisa e startups, que as empresas de energia estão abertas à inovação e que possuem verba disponível para investir em projetos inovadores. Os desafios são os mais diversos, e buscamos com o EFT desenvolver o ecossistema de parceiros para nos apoiar na solução deles.”' },
      { author : 'José Tenório Barreto Junior, Coordenador de Pesquisa, Desenvolvimento e Inovação da Light', text: '“Acreditamos que o momento que o Setor Elétrico passa é de grandes mudanças com consequentes desafios. Assim, a inovação será uma grande alavanca para a superação desses desafios e o evento Energy Future é uma iniciativa que vem abrir mais espaços para novos caminhos que necessitam serem trilhados. O Energy Future pode colaborar com a abertura para novos entrantes no Setor Elétrico, como Startups, que poderão se aliar a esse Setor buscando agregar com novas tecnologias e novas formas de relacionamento com o cliente.”' },
    ]
  }),
  methods: {
      goPrev() {
        (this.activeTestimonial <= 0) ? this.activeTestimonial = 0 : this.activeTestimonial --
      },
      goNext() {
        (this.activeTestimonial >= this.testimonials.length - 1) ? this.activeTestimonial = this.testimonials.length -1 : this.activeTestimonial ++  
      }
  },
  components: { Collapse }    
}
</script>


<style lang="scss">

.lp-hero {

    &__bg {
        @media(min-width: 992px) {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: url("../assets/images/img-graphism-bg.svg");
            background-size: contain;
            background-repeat: no-repeat;
            background-position-y: 2%;
            opacity: .35;
            z-index: -999;   
        }

        @media(min-width: 1500px) {
            transform: translateY(6rem);
        }

        @media(min-width: 2050px) {
            display: none;
        }         
    }

    &__title {
        color: $primary-color !important;
    }

    &__subtitle {
        text-transform: none;
        color: rgba(#011E41, .75);
        font-weight: 400;
    }

    &__title, &__subtitle {
        max-width: 36rem;
    }

    &__button {
        @include colored-button($accent-color-2);
        margin: 1.5rem 0;
        width: 100%;
        text-align: center;
        @media(min-width: 768px) {
            width: 18rem;
        }         
        @media(min-width: 992px) {
            margin-bottom: 0;
        }     
    }

    &__video {
        iframe {
            width: 100%;
            height: 20.5rem;
            @media (min-width: 992px) {
                max-width: 600px;
            }
            box-shadow: 0 20px 30px rgba(#000, .16);
        }
    }
}


.line-title {
    margin: 6rem 0 1.5rem;
    color: $primary-color !important;
    @include news-headline($accent-color-1);

    @media (min-width: 768px) {
        font-size: 1rem;
    }
}

.companies {

    &__list {
        padding-left: 0;
        display: flex;
        flex-wrap: wrap;
        align-items: center;
        justify-content: space-around;
        @media (min-width: 992px) {
            justify-content: space-between;
        }
    }
    &__item {
        padding: 1rem;
        img {
            max-width: 6rem;
            filter: grayscale(100%);
            opacity: .7;
        }         
    }
}

.color-box {
    position: relative;
    background-color: #fff;
    border-radius: .44rem;
    padding: 1rem 1.5rem 1.5rem;
    box-shadow: 0 10px 30px rgba($primary-color, .08);
    margin-top: 3rem;
    overflow: hidden;

    &::before {
        content: "";
        position: absolute;
        width: 100%;
        height: .33rem;
        background-color: $secondary-color;
        top: 0;
        left: 0; 
    }

    &__title {
        margin: 1.5rem 0;
        @media(min-width: 992px) {
            margin-bottom: 3rem;
        }
    }

    &__icon {
        margin: 1.5rem 0 1rem;
        width: 3rem;
        @media(min-width: 992px) {
            margin-top: 0;
        }
    }
    
    &__text {
        text-transform: uppercase;
        font-size: .77rem;
        font-weight: 500;
    }
}

.testimonial {
    padding: 4.5rem 2rem;
    position: relative;
    transition: all .2s ease;

    @media (min-width: 768px) {
        &::before {
            content: "";
            position: absolute;
            width: 100vw;
            top: -1.5rem;
            left: calc(-100vw / 2 + 1125px / 2);
            right: calc(-100vw / 2 + 1125px / 2);  
            background: rgba(#fff, .5);
            //background: linear-gradient(90deg, transparent 0%, #fff 50%, transparent 100%);
            height: 22rem;

            @media (max-width: 1199px) {
                left: calc(-100vw / 2 + 52.5rem / 2);
                right: calc(-100vw / 2 + 52.5rem / 2);    
            }

            @media (max-width: 991px) {
                left: calc(-100vw / 2 + 39.16rem / 2);
                right: calc(-100vw / 2 + 39.16rem / 2);
                height: 20rem;    
            }

            @media (max-width: 767px) {
                left: calc(-100vw / 2 + 29.16rem / 2);
                right: calc(-100vw / 2 + 29.16rem / 2);    
                height: 24rem;
            }

            @media (max-width: 575px) {
                left: calc(-100vw / 2 + 26.11rem / 2);
                right: calc(-100vw / 2 + 26.11rem / 2);
            }

            @media (max-width: 479px) {
                display: none;
            }        
        }
    }

    &__text {
        color: $primary-color;
    }

    &__button {
        position: absolute;
        top: 45%;
        font-size: 1.25rem;
        color: $secondary-color;

        @media(min-width: 768px) {
            font-size: 1.5rem;
        }
        &:hover {
            cursor: pointer;
        }
    }

    &__button.previous {
        left: 0;
    }

    &__button.next {
        right: 0;
    }

}

.new-card {
    padding: 1.5rem 1.5rem;
    background-color: #fff;
    position: relative;
    box-shadow: 0 .5rem 1rem 0 rgba($primary-color, .08);
    border-radius: .55rem;
    overflow: hidden;
    max-width: 22rem;
    transition: box-shadow .2s ease;
    min-height: 18.44rem;   

    &:hover {
        box-shadow: 0 3rem 5rem -1rem rgba($primary-color, .16);
    }

    &::before {
        content: "";
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: .44rem;
    }

    &--1 {
        &::before {
            background-color: $accent-color-2;
        }
    }
    &--2 {
        &::before {
            background-color: $accent-color-1;
        }
    }
    &--3 {
        &::before {
            background-color: $secondary-color;
        }
    } 

    &__icon {
        font-size: 1.5rem;
        color: $primary-color;
        font-weight: bold;
        margin: 1rem 0;
        
        img {
            height: 2.1rem;
        }
    }

    &__title {
        margin-top: 0;
    }

    &__divider {
        width: 100%;
        height: .22rem;
        margin: 1.5rem 0;

        &--1 {
            background-color: rgba($accent-color-2, .12);
        }
        &--2 {
            background-color: rgba($accent-color-1, .12);
        }
        &--3 {
            background-color: rgba($secondary-color, .12);
        }                        
    }

    &__text {
        font-size: .77rem;
        margin-bottom: 3rem;
    }

    &__link {
        display: block;
        font-size: .88rem;
        @media(min-width: 1200px) {
            font-size: .77rem;
            line-height: 1.5;
        }
        font-weight: 500;
        margin-bottom: .5rem;
        color: rgba($primary-color, .87) !important;

        svg {
            margin-right: 1rem;
            @media(min-width: 1200px) {
                margin-right: .5rem;
                // display: none;
            }
        }

        &--1 {
            @media(min-width: 1200px) {
                color: $accent-color-2;
            }
            svg {
                color: $accent-color-2;
            }
            &:hover {
                color: $accent-color-2;
            }
        }
        &--2 {
            @media(min-width: 1200px) {
                color: $accent-color-1;
            }            
            svg {
                color: $accent-color-1;
            }            
            &:hover {
                color: $accent-color-1;
            }
        }
        &--3 {
            @media(min-width: 1200px) {
                color: $secondary-color;
            }            
            svg {
                color: $secondary-color;
            }            
            &:hover {
                color: $secondary-color;
            }
        }
    }
}

.cta-btn {
    margin-top: 6rem;
    @extend .lp-hero__button;
}

.lp-footer {
    margin-top: 6rem;
    position: relative;    
}

.lp-supporters {
    //margin: 1rem;
}

.lp-bottom-logos {
    width: 100%;
}

.lp-footer-link {
    text-transform: uppercase;
    color: #fff !important;
    font-size: .88rem;
    font-weight: 500;
    letter-spacing: .7px;

    svg {
        color: $accent-color-2;
    }

}

.aneel {
    @media (min-width: 768px) {
        transform: translateY(5px);
    }
}

.lp-footer-line {
    position: relative;
    margin-top: 1rem;
    @media (min-width: 576px) { 
        margin-top: 0;
    }     
    &::before {
        content: "";
        position: absolute;
        width: 100%;
        height: 2px;
        top: 45%;
        background-color: rgba(#000, .3);       
    }
}


</style>

