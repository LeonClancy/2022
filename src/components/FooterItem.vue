<template>
  <div>
    <mint-box v-if="!hideSponsor" class="sponsors-items" :class="{ 'is-index': isIndex }">
      <img class="sponsor" :src="'/2022/imgs/logo.png'" />
      <a class="sponsor-item" v-for="item of sponsorsData" :href="item.link" target="_blank">
        <img class="sponsor" :src="`/2022/imgs/sponsors/${item.logo}`" />
      </a>
    </mint-box>
    <div class="footer">
      <img class="footer-cat" :src="'/2022/imgs/cats/cat2.svg'" />

      <div class="title">學生計算機年會</div>
      <div class="title"> Students' Information Technology Conference</div>
      <div class="content">
        <div class="left">

          <div class="title" style="margin-top: 1em">合作聯繫</div>
          <div class="subtitle">
            <a href="mailto:contact@sitcon.org">
              contact@sitcon.org</a>
          </div>
          <div class="title">票務問題</div>
          <div class="subtitle">
            <a href="mailto:ticket@sitcon.org">
              ticket@sitcon.org</a>
          </div>
        </div>
        <div class="right">

          <div class="title">社群媒體</div>
          <div class="social-media-items">
            <a href="https://sitcon.org/fb" target="_blank" class="social-media-item reverse-color">
              <img :src="'/2022/imgs/social-media/facebook.svg'" alt="Facebook" />
            </a>
            <a href="https://sitcon.org/instagram" target="_blank" class="social-media-item">
              <img :src="'/2022/imgs/social-media/instagram.svg'" alt="Instagram" />
            </a>
            <a href="https://sitcon.org/tg" target="_blank" class="social-media-item reverse-color">
              <img :src="'/2022/imgs/social-media/telegram.svg'" alt="Telegram" />
            </a>
            <a href="https://sitcon.org/twitter" target="_blank" class="social-media-item reverse-color">
              <img :src="'/2022/imgs/social-media/twitter.svg'" alt="Twitter" />
            </a>
            <a href="https://sitcon.org/plurk" target="_blank" class="social-media-item">
              <img :src="'/2022/imgs/social-media/plurk.svg'" alt="Plurk" />
            </a>
            <a href="https://sitcon.org/yt" target="_blank" class="social-media-item reverse-color">
              <img :src="'/2022/imgs/social-media/youtube.svg'" alt="YouTube" />
            </a>
            <a href="https://sitcon.org/flickr" target="_blank" class="social-media-item reverse-color">
              <img :src="'/2022/imgs/social-media/flickr.svg'" alt="Flickr" />
            </a>
            <a href="https://sitcon.org/odysee" target="_blank" class="social-media-item">
              <img :src="'/2022/imgs/social-media/odysee.svg'" alt="Odysee" />
            </a>
            <a href="https://sitcon.org/medium" target="_blank" class="social-media-item">
              <img :src="'/2022/imgs/social-media/medium.svg'" alt="Medium" />
            </a>
          </div>
          <div class="title">歷年網站</div>
          <div class="web-items">
            <a v-for="website in websites" :href="website.url" target="_blank" class="web-item">
              {{ website.name }}
            </a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
import { ref } from 'vue';

import sponsors from '@/assets/sponsors.json';
const sponsorsData = ref([
  ...sponsors.co_org,
  ...sponsors.sponsors.map(x => x.org).flat(),
  ...sponsors.thanks.map(x => x.org).flat()
]);
const props = defineProps({
  hideSponsor: {
    type: Boolean,
    default: false
  },
  isIndex: {
    type: Boolean,
    default: false
  },
})
const websites = ref(Array.from({ length: 9 }, (_, i) => ({ name: i + 2013, url: `https://sitcon.org/${i + 2013}` })))
</script>
<style lang="sass" scoped>
.sponsors-items
  margin-top: 48px
  display: grid
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr))
  grid-gap: 20px
  @media (max-width: 768px)
    grid-template-columns: repeat(auto-fit, minmax(125px, 1fr))
  img
    width: 100%


.footer
  --padding: 36px
  margin-top: calc(5px + 80px)
  margin-bottom: var(--padding)
  width: min(1280px,95vw)
  background-color: #82D357
  color: #373737
  position: relative
  border-radius: var(--padding)
  padding: var(--padding)
  z-index: 1
  .footer-cat
    top: calc(36px * -2 + 2px)
    width: 100px
    height: 70px
    object-fit: cover
    object-position: top center
    position: absolute
    right: var(--padding)
    transition: all 0.3s cubic-bezier(.5,-0.55,.53,1.45)
  &:hover
    .footer-cat
      transform: translateY(5px)
      height: 65px
  &:active
    .footer-cat
      transform: translateY(-5px)
      height: 75px
  @media (max-width: 768px)
    --padding: 24px

  .title
    font-size: 20px
    font-weight: bold
    @media (max-width: 768px)
      font-size: 16px
  .subtitle
    font-weight: normal
  .content
    display: grid
    grid-template-columns: 1fr 1fr
    grid-gap: 20px
    font-size: 18px
    align-items: end
    @media (max-width: 768px)
      font-size: 14px
    a
      color: #373737
      transition: all .2s ease
      &:hover
        opacity: .8
      &:active
        opacity: 1
    @media (max-width: 768px)
      grid-template-columns: 1fr
    .social-media-items
      --size: 24px
      display: grid
      grid-template-columns: repeat(auto-fit, var(--size))
      grid-gap: 24px
      margin-bottom: 4px
      .social-media-item
        display: block
        width: var(--size)
        height: var(--size)
        display: flex
        flex-wrap: wrap
        justify-content: center
        align-items: center
        transition: all .2s ease
        &.reverse-color
          img
            filter: invert(.8)
        &:not(.reverse-color)
          img
            opacity: .8
        img
          width: var(--size)
          height: var(--size)
          object-fit: contain
          object-position: center
        &:hover
          opacity: .8
        &:active
          opacity: 1
    .web-items
      display: flex
      flex-wrap: wrap
      gap: 8px
</style>