<script>
import AppBreadcrumbs from '@/components/UI/AppBreadcrumbs.vue'
import DetailCaseIntro from '@/components/DetailCaseIntro.vue'
import NextCase from '@/components/NextCase.vue'
import nextCaseImg from '@/assets/images/mock-content/cases-page-1.png'

export default {
  components: {
    AppBreadcrumbs,
    DetailCaseIntro,
    NextCase
  },
  data() {
    return {
      caseItem: {
        id: 1,
        title: 'Mesh3',
        year: '2022',
        description: 'Mesh3 — фонд, который инвестирует в современные проекты, объединяющие в себе культуру, искусство и технологии',
        links: [
          { name: 'сайт', link: 'https://www.google.com/' },
          { name: 'приложение', link: 'https://www.google.com/' },
          { name: 'кейс на behance', link: 'https://www.google.com/' },
          { name: 'отзыв', link: 'https://www.google.com/' }
        ],
      },
      nextCase: {
        id: 2,
        title: 'Логотип Vybez',
        image: nextCaseImg,
        category: 'брендинг',
        url: '/cases/b2cpl'
      }
    }
  }
}
</script>

<template>
  <div class="container">
    <app-breadcrumbs
      :items="[{ name: 'Кейсы', path: '/cases' }, { name: 'Mesh3' }]" />
    <detail-case-intro :caseItem="caseItem" />
    <section class="visual">
      <div class="wrapper">
        <div class="visual__content">
          <div class="visual__block visual__block--full-width">
            <img
              src="@/assets/images/case-mesh3/box1.jpg"
              alt="img"
            >
          </div>
          <div class="visual__block">
            <img
              src="@/assets/images/case-mesh3/box2.jpg"
              alt="img"
            >
          </div>
          <div class="visual__block">
            <img
              src="@/assets/images/case-mesh3/box3.jpg"
              alt="img"
            >
          </div>
        </div>
      </div>
    </section>
    <next-case :nextCase="nextCase" />
  </div>
</template>

<style lang="scss" scoped>
.visual {
  &__content {
    display: flex;
    flex-wrap: wrap;
    margin-top: 46px;
    justify-content: space-between;
  }

  &__block {
    width: calc(50% - 20px / 2);
    height: 630px;
    background: $color-general-dark;
    border-radius: 32px;
    overflow: hidden;

    img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      object-position: left;
    }

    &--full-width {
      width: 100%;
      height: 725px;
      margin-bottom: 20px;

      img {
        object-fit: contain;
      }
    }
  }
}

@media (max-width: 1400px) {
  .visual {
    &__block--full-width {
      img {
        object-fit: cover;
      }
    }
  }
}

@media (max-width: 1024px) {
  .visual {
    &__content {
      margin-top: 23px;
    }

    &__block {
      width: calc(50% - 8px / 2);
      height: 400px;

      &--full-width {
        width: 100%;
        height: 400px;
        margin-bottom: 8px;
      }
    }
  }
}

@media (max-width: 590px) {
  .visual {
    &__block {
      width: 100%;
      height: 350px;
    }
  }
}
</style>