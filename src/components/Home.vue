<template>
  <div class="home">

    <Title></Title>

    <div class="card-expansion">
      <md-card>
        <md-card-media>
          <img src="../assets/images/demons/chernobog.jpg" alt="Чернобог (Czorneboh, Czernebog)">
        </md-card-media>

        <md-card-header>
          <div class="md-title">Чернобог (Czorneboh, Czernebog)</div>
          <div class="md-subhead">В мифологии балтийских славян злой бог, приносящий несчастье.</div>
        </md-card-header>

        <md-card-expand>
          <md-card-actions md-alignment="space-between">
            <div>
              <md-button>Поделиться</md-button>
            </div>

            <md-card-expand-trigger>
              <md-button>Читать</md-button>
            </md-card-expand-trigger>
          </md-card-actions>
        </md-card-expand>
      </md-card>
    </div>
  </div>
</template>

<script>
import Vue from 'vue';
import VueMaterial from 'vue-material';
import 'vue-material/dist/vue-material.min.css';
import Title from '@/components/common/Title';

Vue.use(VueMaterial);

export default {
  name: 'Home',
  data() {
    return {
      title: 'Gods and Demons',
    };
  },
  components: {
    Title,
  },
};
</script>

<style lang="scss" scoped>
@import url("https://fonts.googleapis.com/css?family=Roboto:400,500,700,400italic|Material+Icons");

.card-expansion {
  height: 480px;
}

.md-card {
  width: 320px;
  margin: 4px;
  display: inline-block;
  vertical-align: top;
}
</style>
