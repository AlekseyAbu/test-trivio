<template>
  <div class="fon" @click="close($event)">
    <div class="profile" :class="{active: show}">
      <span class="profile__name">{{user.name}}</span>
      <span class="profile__company">Тривио</span>
      <span class="profile__balance">баланс: {{user.balance}}</span>
      <span class="profile__arrears">задолженность: {{user.arrears}}</span>
      <a v-for="(item, index) in nav" :key="index" class="profile__item" href="#">{{item}}</a>
      <span class="profile__edit">Выход</span>
    </div>
  </div>
</template>

<script>
export default {
  emits: ['close-modal'],
  data: () => ({
    user: {name: 'aleksey abu', balance: '-597,12 ₽', arrears: '0,00 ₽'},
    nav: ['Профиль', 'Управление', 'Моя компания'],
    show: false
  }),
  mounted() {
    setTimeout(() => this.show = true, 1)
  },
  methods: {
    close(event) {
      if (event === 'close' || event.target.classList.contains('fon')) {
        this.show = false;
        setTimeout(() => this.$emit('close-modal'), 500);
      }
    }
  }
}
</script>

<style lang="scss" scoped>
%text {
  font-family: sans-serif;
  font-style: normal;
  font-weight: normal;
  font-size: 12px;
  line-height: 110%;
  text-decoration: none;
  color: black;
  &:hover {
    opacity: .5;
  }
}
%textGray {
  font-family: sans-serif;
  font-style: normal;
  font-weight: normal;
  font-size: 10px;
  line-height: 110%;
  text-decoration: none;
  color: gray;
}
.fon {
  position: fixed;
  top: 0;
  right: 0;
  left: 0;
  bottom: 0;
}
.profile {
  position: absolute;
  top: 70px;
  right: 30px;
  width: 200px;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  padding: 20px;
  border-radius: 5px;
  opacity: 0;
  transition: 1s;
  background: #fff;
  &__name {
    @extend %text;
    margin-bottom: 10px;
    cursor: pointer;
  }
  &__company {
    @extend %textGray;
  }
  &__balance {
    @extend %textGray;
  }
  &__arrears {
    @extend %textGray;
    margin-bottom: 10px;
  }
  &__item {
    @extend %text;
    margin-bottom: 5px;
  }
  &__edit {
    @extend %text;
    color: red;
    margin-top: 10px;
    cursor: pointer;
  }
}
.active {
  opacity: 1;
  transition: 1s;
}
@media screen and (max-width: 785px) {
  .profile {
    top: 175px;
    right: calc(50% - 100px);
  }
}
@media screen and (max-width: 502px) {
  .profile {
    top: 215px;
  }
}
@media screen and (max-width: 390px) {
  .profile {
    top: 235px;
  }
}
</style>
