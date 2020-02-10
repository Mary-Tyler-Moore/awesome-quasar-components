<template>
  <div>
    <header class="welcome text-white text-center q-my-xl">
      <h1 class="text-h4">Welcome to the A-Q-C (Awesome Quasar Components)</h1>
      <h4 class="text-h6">This is not just a website. This is components world like VueJSExamples.Com</h4>
      <h4 class="text-h6">But in this website you find Quasar-Framework Components</h4>
    </header>
    <q-carousel
      v-model="slide"
      transition-prev="slide-right"
      transition-next="slide-left"
      swipeable
      animated
      control-color="primary"
      arrows
      height="300px"
      class="bg-transparent q-px-xl text-black"
    >
      <q-carousel-slide :name="1" class="column no-wrap">
        <div class="row fit justify-start items-center q-gutter-xs q-col-gutter no-wrap">
          <q-img
            @click="goStepper"
            src="statics/component-images/stepper.PNG"
            style="width: 100%;height:100%;cursor:pointer;"
          >
            <div class="absolute-bottom text-subtitle1 text-center">Awesome stepper with validation</div>
          </q-img>
          <q-img
            @click="goStepper"
            src="statics/comingsoon.png"
            style="width: 100%;height:100%;cursor:pointer;"
          >
            <div class="absolute-bottom text-subtitle1 text-center">Awesome button with an icon</div>
          </q-img>
          <q-img class="col-3 full-height" src="statics/comingsoon.png" />
          <q-img class="col-3 full-height" src="statics/comingsoon.png" />
        </div>
      </q-carousel-slide>
      <q-carousel-slide :name="2" class="column no-wrap">
        <div class="row fit justify-start items-center q-gutter-xs q-col-gutter no-wrap">
          <q-img class="col-3 full-height" src="statics/comingsoon.png" />
          <q-img class="col-3 full-height" src="statics/comingsoon.png" />
          <q-img class="col-3 full-height" src="statics/comingsoon.png" />
          <q-img class="col-3 full-height" src="statics/comingsoon.png" />
        </div>
      </q-carousel-slide>
      <q-carousel-slide :name="3" class="column no-wrap">
        <div class="row fit justify-start items-center q-gutter-xs q-col-gutter no-wrap">
          <q-img class="col-3 full-height" src="statics/comingsoon.png" />
          <q-img class="col-3 full-height" src="statics/comingsoon.png" />
          <q-img class="col-3 full-height" src="statics/comingsoon.png" />
          <q-img class="col-3 full-height" src="statics/comingsoon.png" />
        </div>
      </q-carousel-slide>
    </q-carousel>
    <footer class="welcome text-white text-center q-py-xl">
      <h3 class="text-h3">More contents coming soon</h3>
      <h4 class="text-h4">More contents coming soon</h4>
      <h4 class="text-h6">More contents coming soon</h4>
    </footer>
  </div>
</template>

<script>
// import { openURL } from "quasar";
export default {
  name: "homepage",
  data() {
    return {
      slide: 1,
      autoplay: true
    };
  },
  methods: {
    goStepper() {
      this.$router.push({path: '/stepper'})
    }
  },
};
</script>
