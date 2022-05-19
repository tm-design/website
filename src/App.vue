<script setup lang="ts">
import { RouterLink, RouterView } from "vue-router";
import HelloWorld from "@/components/HelloWorld.vue";
import { computed } from "@vue/reactivity";

var videoID = "YqVjA-6FV4w";
videoID = "cAaW6kNWHV8";
videoID = "S0qHfBs2ASE";
const video = computed(
  () =>
    `https://www.youtube-nocookie.com/embed/${videoID}?controls=0&autoplay=1&mute=1&playlist=${videoID}&loop=1`
);
</script>

<template>
  <Teleport to="body">
    <div id="video-background">
      <iframe
        width="560"
        height="315"
        :src="video"
        title="YouTube video player"
        frameborder="0"
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
        allowfullscreen
      ></iframe>
    </div>
  </Teleport>
  <header>
    <!-- <img
      alt="Vue logo"
      class="logo"
      src="@/assets/logo.svg"
      width="125"
      height="125"
    /> -->

    <div class="wrapper">
      <div id="title">Tim Mudd</div>

      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style lang="sass">
@import "@/assets/base"
@import "@/assets/fonts"

#video-background
  position: absolute
  width: 100vw
  height: 100vh
  top: 0%
  left: 0%
  overflow: hidden
  filter: blur(10px) hue-rotate(35deg)
  opacity: .5
  iframe
    position: absolute
    top: 0%
    left: 0%
    width: 100vw
    height: 100vh
    pointer-events: none
    z-index: -1

@media (min-aspect-ratio: 16/9)
  #video-background
    iframe
      height: 56.25vw

@media (max-aspect-ratio: 16/9)
  #video-background
    iframe
      width: 177.78vh


#app
  max-width: 1280px
  margin: 0 auto
  padding: 2rem
  font-weight: normal
  z-index: 1

header
  line-height: 1.5
  max-height: 100vh

  #title
    @extend %title-font
    font-size: 120px
    line-height: 100px

.logo
  display: block
  margin: 0 auto 2rem

a,
.green
  text-decoration: none
  color: hsla(160, 100%, 37%, 1)
  transition: 0.4s

@media (hover: hover)
  a:hover
    background-color: hsla(160, 100%, 37%, 0.2)

nav
  width: 100%
  font-size: 12px
  text-align: center
  margin-top: 2rem

nav a.router-link-exact-active
  color: var(--color-text)

nav a.router-link-exact-active:hover
  background-color: transparent

nav a
  display: inline-block
  padding: 0 1rem
  border-left: 1px solid var(--color-border)

nav a:first-of-type
  border: 0

@media (min-width: 1024px)
  body
    display: flex
    place-items: center


  #app
    display: grid
    grid-template-columns: 1fr 1fr
    padding: 0 2rem

  header
    display: flex
    place-items: center
    padding-right: calc(var(--section-gap) / 2)

  header .wrapper
    display: flex
    place-items: flex-start
    flex-wrap: wrap

  .logo
    margin: 0 2rem 0 0

  nav
    text-align: left
    margin-left: -1rem
    font-size: 1rem
    padding: 1rem 0
    margin-top: 1rem
</style>
