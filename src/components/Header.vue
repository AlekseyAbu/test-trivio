<template>
   <div class="header">
     <div class="header__left">
       <Icon class="header__left__logo" icon="logoTrivio" bg="#2c3e50" height="30" width="70"/>
       <nav class="header__left__nav">
         <a v-for="(item, index) in menu" :key="index" class="link-nav" href="#">{{item}}</a>
       </nav>
       <a class="service-packages" href="#">
         <Icon class="service-packages__img" icon="basket" bg="#2c3e50" height="10" width="10" />
         Пакеты услуг
       </a>
     </div>
     <div class="header__right">
       <div v-for="(icon, index) in icons" class="header__right__icon" :key="index">
         <Icon :icon="icon.icon" :bg="icon.bg" height="15" width="15"/>
         <div v-if="icon.icon === 'watch'" class="badge">3</div>
         <div v-if="icon.icon === 'man'" class="notif"></div>
       </div>
       <div class="header__right__about" @click="showMenu = !showMenu">
         {{ abbrName }}
         <Profile v-if="showMenu" @close-modal="close"/>
       </div>
       <Icon class="header__right__lang" :icon="lang ? 'ru' : 'us'" height="20" width="20" @click="lang = !lang"/>
     </div>

   </div>
</template>
<script>
import Icon from "../svg/icon";
import Profile from "./Profile";
export default {
  components: {Profile, Icon},
  data: () => ({
    menu: ['Рабочий стол', 'Проекты', 'Мои вложения', 'Документы'],
    icons: [{icon: 'zoom', bg: '#f5deb3'}, {icon: 'gallery', bg: '#90ee90'}, {icon: 'watch', bg: '#b0e0e6'}, {icon: 'draw', bg: '#dda0dd'}, {icon: 'man', bg: '#fa8072'}],
    abbrName: 'aa',
    lang: true,
    showMenu: false
  }),
  methods: {
    close() {
      this.showMenu = false
    }
  }
}
</script>

<style lang="scss" scoped>
%layout {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
}
%link {
  font-family: sans-serif;
  font-style: normal;
  font-weight: normal;
  font-size: 12px;
  line-height: 110%;
  text-decoration: none;
  color: black;
}
%btn {
  padding: 10px;
  border-radius: 10px;
  background: #d3d3d3;
  transition: 1s;
  &:hover {
    background: #f5f5f5;
  }
}

.header {
  @extend %layout;
  padding: 10px 30px;
  background: #fff;
  &__left {
    @extend %layout;
    &__logo {
      margin-right: 20px;
    }
  }
  &__right {
    @extend %layout;
    &__icon {
      @extend %layout;
      margin-right: 10px;
      cursor: pointer;
      position: relative;
      transition: 1s;
      &:hover {
        @extend %btn;
        background: #f5f5f5;
      }
    }
    &__about {
      @extend %btn;
      margin-right: 10px;
      cursor: pointer;
    }
    &__lang {
      border-radius: 50%;
      cursor: pointer;
    }
  }
}
.service-packages {
  @extend %layout;
  @extend %link;
  @extend %btn;
  &__img {
    margin-right: 5px;
  }
}
.link-nav {
  @extend %link;
  margin-right: 10px;
  transition: 1s;
  &:hover {
    @extend %btn;
    background: #f5f5f5;
  }
}
.badge {
  position: absolute;
  top: -2px;
  right: 0;
  font-size: 6px;
  font-family: sans-serif;
  font-style: normal;
  font-weight: bold;
}
.notif {
  position: absolute;
  top: -2px;
  right: 0;
  width: 4px;
  height: 4px;
  border-radius: 50%;
  background: red;
}
@media screen and (max-width: 785px){
  .header {
    flex-direction: column;
    &__left {
      flex-wrap: wrap;
      justify-content: center;
      margin-bottom: 20px;
      &__logo {
        flex-basis: 100%;
        margin-bottom: 20px;
        margin-right: 0;
      }
    }
  }
}
@media screen and (max-width: 502px) {
  .header {
    &__left {
      &__nav {
        margin-bottom: 20px;
        display: flex;
        align-items: center;
        justify-content: center;
        flex-wrap: wrap;
      }
    }
  }
  .link-nav {
    margin-bottom: 5px;
  }
}

</style>
