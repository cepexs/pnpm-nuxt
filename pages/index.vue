/* eslint-disable no-console */
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
            :disable3d="true"
            :width="200"
            :height="180"
            :space="210"
            :speed="200"
            :loop="false"
            :count="5"
            :perpective="0"
            :center="false"
          >
            <slide v-for="i in slide" :key="i" :index="i">
              {{ i }}
            </slide>
          </carousel-3d>
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
export default {
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
</style>
