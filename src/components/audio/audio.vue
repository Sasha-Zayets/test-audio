<template>
  <div class="audio">
    <div class="audio__block">
      <div
        class="audio__item"
        v-for="item in audio"
        :key="item.title"
        >
        <div class="audio__play">
          <i class="fa fa-play"></i>
        </div>
        <div class="audio__title">
          {{item.title}}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    audio: [
      {
        title: 'Поздравление с Днём Рождения (звонок из полиции)'
      },
      {
        title: 'С Днём рождения тебя, дорогая моя!'
      },
      {
        title: 'Пускай идут года - ты только молодей!'
      },
      {
        title: 'Я поднимаю за тебя бокал!'
      },
      {
        title: 'Я поднимаю за тебя бокал!'
      }
    ]
  })
}
</script>

<style scoped lang="scss">
.audio {
  padding: 10px;

  &__block {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
  }

  &__item {
    box-shadow: 0px 3px 1px -2px rgba(0,0,0,0.2), 0px 2px 2px 0px rgba(0,0,0,0.14), 0px 1px 5px 0px rgba(0,0,0,0.12);
    width: calc(50% - 20px);
    display: flex;
    align-items: center;
    padding: 10px 5px 10px 10px;
    margin-bottom: 20px;
    &:nth-child(even) {
      margin-left: 5px;
    }
    &:nth-child(odd) {
      margin-right: 5px;
    }
  }

  &__play {
    min-width: 50px;
    margin-right: 10px;
    height: 50px;
    border-radius: 50%;
    display: flex;
    justify-content: center;
    align-items: center;
    background: #1976D2;
    color: white;
    font-size: 20px;
  }

  &__title {
    color: #227BD3;
    font-weight: bold;
  }
}
</style>
