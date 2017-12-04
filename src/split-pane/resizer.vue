<template>
    <div :class="classes"></div>
</template>

<script>
  export default {
    props: {
      split: {
        validator(value) {
          return ['vertical', 'horizontal'].indexOf(value) >= 0
        },
        required: true
      },
      className: String
    },
    data() {
        return {}
    },
    computed: {
      classes: function() {
        const classes = ['Resizer', this.split, this.className];

        return classes.join(' ');
      }
    }
  }
</script>

<style scoped>
.Resizer {
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
  position: absolute;
  -moz-background-clip: padding;
  -webkit-background-clip: padding;
  background-clip: padding-box;
  z-index: 1000;
  background: black
}
.Resizer:hover {
  background: grey
}

.Resizer:after {
  content: "";
  display: block;
  position: absolute;
  background: #fff;
}

.Resizer:hover:after {
  background: darkgrey
}

.Resizer.horizontal:after {
  top: 25%;
  left: 50%;
  width: 24px;
  height: 2px;
}

.Resizer.vertical:after {
  top: 50%;
  left: 25%;
  width: 2px;
  height: 24px;
}

.Resizer.horizontal {
  margin: -5px 0;
  cursor: row-resize;
  width: 100%;
  height: 6px;
  border: 1px #afafaf solid;
  margin-top: 0;
}

.Resizer.vertical {
  height: 100%;
  margin-left: -5px;
  cursor: col-resize;
  width: 6px;
  border: 1px #bdbdbd solid;
  margin-left: -3px;
}
</style>
