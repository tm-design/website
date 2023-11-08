<script setup lang="ts">
import WelcomeItem from "./WelcomeItem.vue";
import DocumentationIcon from "./icons/IconDocumentation.vue";
import ToolingIcon from "./icons/IconTooling.vue";
</script>

<template>
  <WelcomeItem>
    <template #icon>
      <ToolingIcon />
    </template>
    <template #heading>Programmer</template>

    <h2>Welcome to my web and programming portfolio site!</h2>
    <br />
    <h4>
      My name is Tim, and I'm thrilled to share my passion for web development
      and programming with you. I have always been drawn to technology and the
      possibilities it presents. From my early days playing video games on my
      NES at the age of 3, to tinkering with circuit boards and programming at
      the age of 11, I have always been fascinated with the world of tech. As I
      grew older, my love for technology only intensified, and I found myself
      spending countless hours learning everything I could about programming
      languages, web development frameworks, and software engineering best
      practices. Today, I am proud to say that I have turned my passion into a
      career and many custom web applications and responsive websites.
    </h4>
    <br />
    <h4>
      Please note that the site is currently undergoing a major reconstruction
      as I update both the overall design and the projects that I'm working on.
      I apologize for any inconvenience this may cause, but I believe it's
      essential to keep my portfolio fresh and up-to-date to showcase my most
      recent work. Please bear with me during this process, and feel free to
      reach out if you have any questions or would like to learn more about my
      services. Thank you for your patience, and I look forward to unveiling the
      new and improved portfolio soon!
    </h4>
    <br />
    <h3>I can't wait to see where my next programming adventure takes me!</h3>
    <br />
    <h1>- Tim Mudd</h1>
  </WelcomeItem>
</template>

<style lang="sass" scoped>
.signature
  filter: invert(70%)
  width: 300px
  height: auto
</style>
