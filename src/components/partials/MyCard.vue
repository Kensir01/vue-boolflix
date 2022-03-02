<template>
  <li class="col col-md-6 col-lg-4 col-xl-3 cards overflow">
      <div class="content" :style="{ backgroundImage: getBackgroundImage(info.poster_path)}">
          <div class="description">
              <ul>
                  <li>
                      TITOLO: {{getTitle()}}
                  </li>
                  <li>
                      TITOLO ORIGINALE: {{info.original_title}}
                  </li>
                  <li>
                      LINGUA ORIGINALE: <lang-flag :iso="info.original_language"></lang-flag>
                  </li>
                  <li>
                      VOTO:
                      <i v-for="i in 5" :key="i" class="fa-star" :class="(i < getComputedStar)?'fa-solid':'fa-regular'"></i>
                  </li>
                  <li>
                      TRAMA: {{info.overview}}
                  </li>
              </ul>
          </div>
      </div>
  </li>
  <!-- <li class="col col-md-6 col-lg-4 col-xl-3 cards overflow">
    <div>{{getTitle()}}</div>
    <div>{{info.original_title}}</div>

    <img v-if="info.poster_path" :src="`https://image.tmdb.org/t/p/w342/${info.poster_path}`">
    <img v-else :src="require('../../assets/img/no_pic.jpg')">

    <div>
        <lang-flag :iso="info.original_language"></lang-flag>
    </div>
    
    <div>
        <i v-for="i in 5" :key="i" class="fa-star" :class="(i < getComputedStar)?'fa-solid':'fa-regular'"></i>
    </div>

  </li> -->
</template>

<script>
export default {
    name: 'MyCard',
    props: {
        'info': Object
    },
    computed: {
        getComputedStar() {
            return Math.ceil(this.info.vote_average /2);
        }
    },
    methods: {
        getTitle () {
            if (this.info.title) {
                return this.info.title;
            } else {
                return this.info.name;
            }
        },
        getBackgroundImage() {
            if (this.info.poster_path) {
                
                return `url(https://image.tmdb.org/t/p/w342/${this.info.poster_path})` 

            } else {
                
                return `url(https://www.publicdomainpictures.net/pictures/280000/nahled/not-found-image-15383864787lu.jpg)`
                
            }
        }
    }
}
</script>

<style scoped lang="scss">

@import "../../assets/style/variabili.scss";
@import "../../assets/style/generali.scss";


    .cards {
        height: 300px;
        margin: 20px 0px;
        display: inline-block;


        .card {
            background-size: cover;
            background-repeat: no-repeat;
            background-position: center;
        }

        .content {
            height: 100%;
            width: 60%;
            background-repeat: no-repeat;
            background-size: contain;
            background-position: center;
            border-radius: 5px;
            overflow-y: auto;
            position: relative;

            .description {
                background-color: $dark;
                font-size: 13px;
                display: none;
                min-height: 300px;
                padding: 10px;
                position: absolute;
                left: 0;
                right: 0;
                top: 0;

                ul {
                    list-style: none;
                    padding: 0;

                    li {
                    margin: 5px 0px;
                    text-align: left;
                    }
                }
            }

        }

          .content:hover .description {
                display: block;
                cursor: pointer;
                border: 3px solid $light;
                border-radius: 5px;
            }
    }
</style>