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
      <div class="tabs__prev" @click="prevTab()">
        <i class="fa fa-angle-left" v-if="prevShow"></i>
      </div>
      <div class="tabs__container">
        <div
          v-for="item in tabsTitle"
          :key="item.title"
          class="tabs__item"
          :class="{active: item.activeClass}"
          @click="clickTabs(item)"
        >
          <span>{{item.title}}</span>
        </div>
      </div>
      <div class="tabs__next" @click="nextTab()">
        <i class="fa fa-angle-right" v-if="nextShow"></i>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    title: 'Популярные поздравления',
    prevShow: false,
    nextShow: true,
    lastPosition: 0,
    positionElement: 0,
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
      },
      {
        title: 'Девушке2',
        activeClass: false
      },
      {
        title: 'Девушке3',
        activeClass: false
      }
    ]
  }),
  mounted () {
    let items = document.querySelectorAll('.tabs__item')

    items.forEach((el, index) => {
      if (items.length - 1 === index) {
        el.setAttribute('id', 'last')
      }
    })

    let pos = document.querySelector('#last')
    this.lastPosition = pos.offsetLeft
  },
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
    },
    nextTab () {
      let container = document.querySelector('.tabs__container')
      let items = document.querySelectorAll('.tabs__item')
      let element = document.querySelector('.tabs__item')
      let widthElement = element.offsetWidth
      this.positionElement += widthElement

      items.forEach((el, index) => {
        el.style.cssText = `left: ${-this.positionElement}px;`
      })

      this.prevShow = true
      let pos = document.querySelector('#last')
      let spanPost = document.querySelector('#last span')
      this.lastPosition = pos.offsetLeft
      if (this.lastPosition + spanPost.offsetLeft < container.offsetWidth) {
        this.nextShow = false
      }
    },
    prevTab () {
      let items = document.querySelectorAll('.tabs__item')
      let element = document.querySelector('.tabs__item')
      let widthElement = element.offsetWidth
      this.positionElement -= widthElement

      items.forEach((el, index) => {
        el.style.cssText = `left: ${-this.positionElement}px;`
        if (!this.nextShow) {
          this.nextShow = true
        }
      })
      if (element.offsetLeft === 0) {
        this.prevShow = false
      }
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
    justify-content: space-between;

    &__container {
      flex-grow: 1;
      display: flex;
      justify-content: space-between;
      position: relative;
      overflow: hidden;
    }

    &__item {
      position: relative;
      cursor: pointer;
      min-width: calc(100% / 6);
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
      // position: absolute;
      // right: -15px;
      // top: 50%;
      // transform: translateY(-50%);
      @include prevNext(left);
    }

    @media (max-width: 699px) {
      &__item {
        min-width: calc(100% / 4);
      }
    }
    @media (max-width: 510px) {
      &__item {
        min-width: calc(100% / 2);
      }
    }
  }
}
</style>
