<template lang="html">
  <div class="top">
    <div class="top__title">
      <h1>
          {{title}}
      </h1>
    </div>

    <div
      class="tabs"
      >
      <div class="tabs__prev">
        <i class="fa fa-angle-left" v-if="prevShow"></i>
      </div>
      <div
        v-for="item in tabsTitle"
        :key="item.title"
        class="tabs__item"
        :class="{active: item.activeClass}"
        @click="clickTabs(item)"
      >
        {{item.title}}
      </div>
      <div class="tabs__next">
        <i class="fa fa-angle-right"></i>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    title: 'Популярные поздравления',
    prevShow: false,
    tabsTitle: [
      {
        title: 'По именам',
        activeClass: false
      },
      {
        title: 'Популярные',
        activeClass: true
      },
      {
        title: 'Прыкольные',
        activeClass: false
      },
      {
        title: 'Мужчине',
        activeClass: false
      },
      {
        title: 'Женщине',
        activeClass: false
      },
      {
        title: 'Девушке',
        activeClass: false
      }
    ]
  }),
  methods: {
    clickTabs (element) {
      let itemArray = this.tabsTitle
      itemArray.forEach((el) => {
        if (el.activeClass === true) {
          el.activeClass = false
        }
      })
      element.activeClass = true
      this.title = element.title + ' поздравления'
    }
  }
}
</script>

<style lang="scss" scoped>
@mixin prevNext($value) {
  margin-#{$value}: 10px;
  color: white;
  cursor: pointer;
  font-size: 18px;
  width: 9px;
}
.top {
  background: #1976D2;
  padding: 20px 10px 0 10px;

  &__title {
    padding-bottom: 30px;

      h1 {
        color: white;
        font-size: 20px;
        margin: 0;
      }
  }

  .tabs {
    display: flex;
    justify-content: space-around;

    &__item {
      cursor: pointer;
      width: calc(100% / 6);
      text-align: center;
      color: white;
      font-size: 16px;
      opacity: 0.7;
      padding-bottom: 10px;
      border-bottom: 2px solid #1976D2;
      &.active {
        opacity: 1;
        border-bottom: 2px solid #FFEE58;
      }
    }
    &__prev {
      @include prevNext(right);
    }

    &__next {
      @include prevNext(left);
    }
  }
}
</style>
