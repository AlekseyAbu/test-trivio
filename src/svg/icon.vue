<template>
  <svg class='icon' :style="{'height': height+'px', 'width': width+'px', 'fill': bg}">
    <use :xlink:href='`#${icon}`' />
  </svg>
</template>

<script>
export default {
  props: {
    icon: {
      type: String,
      default: ''
    },
    height: {
      type: String,
      default: '16'
    },
    width: {
      type: String,
      default: '16'
    },
    bg: {
      type: String,
      default: 'white'
    }
  }
}

</script>
