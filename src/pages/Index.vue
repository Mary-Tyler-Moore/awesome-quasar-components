<template>
  <div>
    <q-carousel
      v-model="slide"
      transition-prev="slide-right"
      transition-next="slide-left"
      swipeable
      animated
      control-color="primary"
      arrows
      height="300px"
      class="bg-black q-px-xl text-black"
    >
      <q-carousel-slide :name="1" class="column no-wrap">
        <div class="row fit justify-start items-center q-gutter-xs q-col-gutter no-wrap">
          <q-img
            onclick="location.href='/stepper';"
            src="https://cdn.quasar.dev/img/parallax2.jpg"
            style="width: 100%;height:100%;cursor:pointer;"
          >
            <div class="absolute-bottom text-subtitle1 text-center">Awesome button with an icon</div>
          </q-img>
          <q-img
            onclick="location.href='/stepper';"
            src="https://cdn.quasar.dev/img/parallax2.jpg"
            style="width: 100%;height:100%;cursor:pointer;"
          >
            <div class="absolute-bottom text-subtitle1 text-center">Awesome button with an icon</div>
          </q-img>
          <q-img class="col-3 full-height" src="https://cdn.quasar.dev/img/mountains.jpg" />
          <q-img class="col-3 full-height" src="https://cdn.quasar.dev/img/parallax1.jpg" />
        </div>
      </q-carousel-slide>
      <q-carousel-slide :name="2" class="column no-wrap">
        <div class="row fit justify-start items-center q-gutter-xs q-col-gutter no-wrap">
          <q-img class="col-3 full-height" src="https://cdn.quasar.dev/img/parallax2.jpg" />
          <q-img class="col-3 full-height" src="https://cdn.quasar.dev/img/quasar.jpg" />
          <q-img class="col-3 full-height" src="https://cdn.quasar.dev/img/parallax2.jpg" />
          <q-img class="col-3 full-height" src="https://cdn.quasar.dev/img/quasar.jpg" />
        </div>
      </q-carousel-slide>
      <q-carousel-slide :name="3" class="column no-wrap">
        <div class="row fit justify-start items-center q-gutter-xs q-col-gutter no-wrap">
          <q-img class="col-3 full-height" src="https://cdn.quasar.dev/img/cat.jpg" />
          <q-img class="col-3 full-height" src="https://cdn.quasar.dev/img/linux-avatar.png" />
          <q-img class="col-3 full-height" src="https://cdn.quasar.dev/img/cat.jpg" />
          <q-img class="col-3 full-height" src="https://cdn.quasar.dev/img/linux-avatar.png" />
        </div>
      </q-carousel-slide>
    </q-carousel>
  </div>
</template>

<script>
export default {
  data() {
    return {
      slide: 1
    };
  }
};
</script>
