<template>
  <div class="container">
    <div>
      <div class="test">
        <Logo />
        <h1 class="title">
          pnpm-nuxt
        </h1>
      </div>
      <div class="test" data-aos="fade-left" data-aos-duration="2000">
        <h1>Carousel 3D</h1>
        <client-only>
          <carousel-3d
            :per-page="5"
            :space="365"
            :width="360"
            :loop="true"
            :disable3d="false"
          >
            <slide v-for="(n, i) in slide" :key="i" :index="i">
              {{ n }}
            </slide>
          </carousel-3d>
        </client-only>
      </div>
      <div class="test">
        <h1>Flickity</h1>
        <client-only>
          <Flickity ref="flickity" :options="flickityOptions">
            <div class="carousel-cell">
              1
            </div>
            <div class="carousel-cell">
              2
            </div>
            <div class="carousel-cell">
              3
            </div>
            <div class="carousel-cell">
              4
            </div>
            <div class="carousel-cell">
              5
            </div>
          </Flickity>
        </client-only>
      </div>
      <div
        class="test"
        data-aos="flip-left"
        data-aos-easing="ease-out-cubic"
        data-aos-duration="2000"
      >
        <h1>Vue Quill Editor</h1>
        <client-only>
          <quill-editor
            ref="editor"
            v-model="content"
            :options="editorOption"
          />
        </client-only>
      </div>
    </div>
  </div>
</template>

<script>
// import flickity from 'vue-flickity'
export default {
  components: {
    // flickity
  },
  data () {
    return {
      slide: 5,
      content: '<p>I am Example</p>',
      editorOption: {
        // Some Quill options...
        theme: 'snow',
        modules: {
          toolbar: [
            ['bold', 'italic', 'underline', 'strike'],
            ['blockquote', 'code-block']
          ]
        }
      },
      flickityOptions: {
        initialIndex: 0,
        prevNextButtons: false,
        pageDots: true,
        wrapAround: false,
        freeScroll: true,
        contain: true
      }
    }
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}

.test {
  min-height: 200px;
  border: 1px solid red;
  border-radius: 20px;
  padding: 40px;
  margin-bottom: 500px;
}

.test:first-child{
  margin-top: 200px;
}

.carousel {
  width: 300px;
}

.carousel-cell {
  width: 70%;
  height: 200px;
  margin-right: 10px;
  background: #8C8;
  border-radius: 5px;
  counter-increment: gallery-cell;
}

.carousel-cell:before {
  display: block;
  text-align: center;
  content: counter(gallery-cell);
  line-height: 200px;
  font-size: 80px;
  color: white;
}

/* position dots in carousel */
.flickity-page-dots {
  bottom: 0px;
}
/* white circles */
.flickity-page-dots .dot {
  width: 12px;
  height: 12px;
  opacity: 1;
  background: transparent;
  border: 2px solid white;
}
/* fill-in selected dot */
.flickity-page-dots .dot.is-selected {
  background: white;
}

</style>
