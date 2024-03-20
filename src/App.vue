<script setup lang="ts">
import { RouterLink, RouterView } from "vue-router";
import AnimatedBackground from "./components/AnimatedBackground.vue";
</script>

<template>
  <header>
    <div class="wrapper">
      <div id="title">
        Tim Mudd
        <div class="socials">
          <a class="no-hover" href="https://github.com/tm-design">
            <img
              class="social-link"
              src="@/assets/github-mark-white.png"
              alt="Github Logo"
            />
          </a>
          <a class="no-hover" href="https://www.linkedin.com/in/tim-mudd/">
            <img
              class="social-link"
              src="@/assets/LI-In-Bug.png"
              alt="LinkedIn Logo"
            />
          </a>
        </div>
      </div>
      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">Experience</RouterLink>
        <RouterLink to="/projects">Projects</RouterLink>
        <RouterLink to="/contact">Contact</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style lang="sass">
@import "@/assets/base"
@import "@/assets/fonts"

.background
  position: absolute
  width: 100vw
  height: 100vh
  top: 0%
  left: 0%
  overflow: hidden
  filter: blur(10px) hue-rotate(35deg)
  opacity: .5
  z-index: -1
  pointer-events: none
  div
    height: 100%
    width: 100%
    margin: 0
    padding: 0
    iframe
      position: absolute
      top: 0%
      left: 0%
      width: 100vw
      height: 100vh

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
    display: flex

.logo
  display: block
  margin: 0 auto 2rem

a,
.green
  text-decoration: none
  color: hsla(160, 100%, 37%, 1)
  transition: 0.4s

.socials
  display: flex
  margin-left: 30px
  .social-link
    max-height: 27px
    margin-right: 15px
    filter: saturate(0) contrast(0)  brightness(2.2)



@media (hover: hover)
  a:hover:not(.no-hover)
    background-color: hsla(160, 100%, 37%, 0.2)

nav
  width: 100%
  font-size: 1.5rem
  text-align: center
  margin-top: 2rem
  margin-bottom: 2rem
  display: flex
  // justify-content: space-between

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
    padding-top: 20px

  #app
    display: grid
    grid-template-columns: 1fr
    padding: 0 2rem

  header
    display: flex
    place-items: center
    padding-right: calc(var(--section-gap) / 2)

  header .wrapper
    display: flex
    place-items: flex-start
    flex-wrap: wrap
    flex-direction: column

  .logo
    margin: 0 2rem 0 0

  nav
    text-align: left
    margin-left: -0.9rem
    font-size: 1.5rem
    padding: 1rem 0
    margin-top: 1rem
</style>
