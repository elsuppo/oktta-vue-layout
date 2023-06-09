<script>
import { Swiper, SwiperSlide } from 'swiper/vue'
import SwiperCore, { Mousewheel } from 'swiper'
import 'swiper/css'

SwiperCore.use([Mousewheel])
export default {
  props: {
    items: {
      type: Array,
      default() {
        return []
      }
    }
  },
  methods: {
    sliderRight() {
      const sliderBlock = document.querySelector('.slider')
      const swiper = sliderBlock.querySelector('.swiper').swiper
      swiper.slideNext()
    },
    sliderLeft() {
      const sliderBlock = document.querySelector('.slider')
      const swiper = sliderBlock.querySelector('.swiper').swiper
      swiper.slidePrev()
    },
  },
  components: {
    Swiper,
    SwiperSlide
  }
}
</script>

<template>
  <div class="slider">
    <div class="slider__buttons">
      <button @click="sliderLeft">
        <svg>
          <use xlink:href="@/assets/icons/_sprite.svg#slider-left" />
        </svg>
      </button>
      <button @click="sliderRight">
        <svg>
          <use xlink:href="@/assets/icons/_sprite.svg#slider-right" />
        </svg>
      </button>
    </div>
    <swiper
      :slidesPerView="'auto'"
      :mousewheel="{
        releaseOnEdges: true
      }"
      :grabCursor="true"
    >
      <swiper-slide
        v-for="item in items"
        :key="item.id"
        class="slider__item"
      >
        <div
          :style="{ background: `center / cover no-repeat url(${item.image})` }"
          class="slider__item-cover"
        ></div>
        <div class="slider__item-title">
          <span>({{ item.id < 10 ? `0${item.id}` : item.id }})</span>
          <h3>{{ item.title }}</h3>
        </div>
        <p class="slider__item-description">{{ item.description }}</p>
      </swiper-slide>
    </swiper>
  </div>
</template>

<style lang="scss" scoped>
.slider {
  position: relative;

  &__item {
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    border-right: 1px solid $color-divider;
    padding: 0 8px;

    &:first-child {
      padding-left: 0;
    }

    &:last-child {
      padding-right: 0;
      border-right: none;
    }

    &-cover {
      width: 380px;
      height: 260px;
      border-radius: 21px;
    }

    &-title {
      display: flex;
      margin-top: 12px;
      max-width: 98%;

      span {
        font: $font-small-playfair;
        font-size: 13px;
        line-height: 125%;
        // font-variant-numeric: lining-nums;
      }

      h3 {
        font: $font-h3-gilroy;
        letter-spacing: -0.04em;
        margin: 0 0 12px 4px;
      }
    }

    &-description {
      color: $color-text-secondary;
      letter-spacing: -0.03em;
      max-width: 98%;
    }
  }

  &__buttons {
    display: flex;
    align-items: center;
    position: absolute;
    right: 30px;
    top: -104px;

    button {
      width: 48px;
      height: 48px;
      display: flex;
      align-items: center;
      justify-content: center;
      border: 1px solid $color-divider;
      border-radius: 50%;
      background: inherit;
      cursor: pointer;
      transition: background 0.2s ease-in-out, border 0.2s ease-in-out;

      svg {
        width: 10px;
        height: 10px;
        stroke: $color-general-black;
        transition: stroke 0.2s ease-in-out;
      }

      &:first-child {
        margin-right: 12px;
      }

      &:hover {
        border: 1px solid $color-general-dark;
        background: $color-general-dark;

        svg {
          stroke: $color-general-white;
        }
      }
    }
  }
}

.swiper {
  width: 100%;
  height: 100%;
  padding: 0 30px;
}

.swiper-slide {
  width: 397.5px;
  height: 404px;

  &:first-child,
  &:last-child {
    width: 389.5px;
  }
}

@media (max-width: 1024px) {
  .slider {
    &__item {
      &-cover {
        width: 330px;
        height: 218px;
      }

      &-title {
        span {
          font-size: 10px;
        }

        h3 {
          font-size: 24px;
        }
      }
    }

    &__buttons {
      display: none;
    }
  }

  .swiper {
    padding: 0 20px;
  }

  .swiper-slide {
    width: 347.5px;
    height: 346px;

    &:first-child,
    &:last-child {
      width: 339.5px;
    }
  }
}

@media (max-width: 590px) {
  .swiper {
    padding: 0 16px;
  }
}
</style>
