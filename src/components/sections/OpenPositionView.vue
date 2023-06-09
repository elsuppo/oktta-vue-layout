<script>
import CardTags from '@/components/CardTags.vue'

export default {
  components: {
    CardTags,
  },
  props: {
    position: {
      type: Object
    }
  }
}
</script>

<template>
  <section class="section">
    <div class="wrapper">
      <div class="section__content">
        <div class="section__block">
          <div class="position-info">
            <h1 class="position-title">
              {{ position.title }}
            </h1>
            <button class="position-button position-button--small">
              откликнуться
            </button>
          </div>
        </div>
        <div class="section__block">
          <div class="position-info">
            <div class="position-tags">
              <card-tags :tags="position.tags" />
            </div>
            <div class="position-info-block">
              <h3 class="position-list-title">Чем нужно будет заниматься:</h3>
              <ul class="position-list">
                <li
                  v-for="(task, index) in position.tasks"
                  :key="index"
                  class="position-list-item"
                >
                  <span class="position-list-marker">—</span>
                  {{ task }}
                </li>
              </ul>
            </div>
            <div class="position-info-block">
              <h3 class="position-list-title">Чего ждём от тебя:</h3>
              <ul class="position-list">
                <li
                  v-for="(requirement, index) in position.requirements"
                  :key="index"
                  class="position-list-item"
                >
                  <span class="position-list-marker">—</span>
                  {{ requirement }}
                </li>
              </ul>
            </div>
            <div class="position-info-block">
              <h3 class="position-list-title">Условия:</h3>
              <ul class="position-list">
                <li
                  v-for="(condition, index) in position.conditions"
                  :key="index"
                  class="position-list-item"
                >
                  <span class="position-list-marker">—</span>
                  {{ condition }}
                </li>
              </ul>
            </div>
          </div>
        </div>
        <button class="position-button position-button--fullwidth">
          откликнуться
        </button>
      </div>
    </div>
  </section>
</template>

<style lang="scss" scoped>
.section {
  &__content {
    display: flex;
    justify-content: space-between;
  }
}

.position {
  &-title {
    font: $font-page-title-gilroy;
    letter-spacing: -0.04em;
    margin-bottom: 16px;
  }

  &-info {
    display: flex;
    flex-direction: column;

    &-block {
      display: flex;
      flex-direction: column;
    }
  }

  &-list {
    list-style-type: none;
    display: flex;
    flex-direction: column;
    padding-right: 24px;

    &-title {
      font: $font-h3-gilroy;
      letter-spacing: -0.04em;
      margin: 16px 0;
    }

    &-marker {
      font: 400 13px/1.25 "Playfair Display", serif;
      margin-right: 8px;
    }

    &-item {
      font-size: 14px;
      color: $color-text-secondary;
      line-height: 1.5;
      letter-spacing: -0.03em;
      display: flex;
      margin-bottom: 8px;

      &:last-child {
        margin-bottom: 0;
      }
    }
  }

  &-button {
    height: 52px;
    border-radius: 40px;
    border: 1px solid $color-general-green;
    color: $color-general-dark;
    background: $color-general-green;
    font: $font-button;
    letter-spacing: -0.03em;
    cursor: pointer;
    transition: background 0.2s ease-in-out, border 0.2s ease-in-out;
    display: flex;
    align-items: center;
    justify-content: center;

    &:hover {
      background: $color-general-white;
      border: 1px solid $color-general-dark;
    }

    &:active {
      border: 1px solid $color-divider;
    }

    &--small {
      width: 167px;
    }

    &--fullwidth {
      display: none;
      width: 100%;
    }
  }
}

@media (max-width: 1280px) {
  .position {
    &-list {
      max-width: 500px;
      padding-right: 0;
    }
  }
}

@media (max-width: 1024px) {
  .section {
    &__content {
      display: flex;
      justify-content: flex-start;
      flex-direction: column;
    }
  }

  .position {
    &-title {
      font-size: 40px;
    }

    &-list {
      max-width: 100%;

      &-title {
        font-size: 24px;
      }
    }

    &-button {
      &--small {
        display: none;
      }

      &--fullwidth {
        display: flex;
        margin: 40px 0;
      }
    }
  }
}

@media (max-width: 590px) {
  .position {
    &-title {
      font-size: 32px;
    }
  }
}
</style>