<template>
  <div class="avatar" v-bind:style="style">
    <table>
      <tr>
        <td v-if="!hasImage">{{initials}}</td>
      </tr>
    </table>
  </div>
</template>

<script>
  export default {
    name: 'avatar',
    props: {
      fullname: { type: String, default: '##' },
      size: { type: Number, default: 48 },
      radius: { type: Number, default: 50 },
      color: { type: String, default: '' },
      image: { type: String, default: '' }
    },
    computed: {
      // compute initials from fullname
      initials () {
        var words = this.fullname.split(/[\s-]+/)
        var intls = ''
        for (var i = 0; i < words.length; i++) {
          intls += words[i].substr(0, 1).toUpperCase()
        }
        if (intls.length > 3) {
          intls = intls.substr(0, 3)
        }
        return intls
      },
      // compute style from props
      style () {
        var fontSize = this.initials.length > 2 ? this.size / 3 : this.size / 2
        this.radius = this.radius >= 0 ? this.radius : 0
        this.radius = this.radius <= 50 ? this.radius : 50
        return {
          'width': this.size + 'px',
          'height': this.size + 'px',
          'border-radius': this.radius + '%',
          'font-size': fontSize + 'px',
          'background-color': this.color == '' ? this.toColor(this.fullname) : this.color,
          'background-image': this.hasImage ? 'url(' + this.image + ')' : 'none'
        }
      },
      hasImage () {
        return (this.image != '')
      }
    },
    methods: {
      toColor (str) {
        var hash = 0
        var len = str.length
        if (len === 0) return black
        for (var i = 0; i < len; i++) {
          hash = ((hash << 8) - hash) + str.charCodeAt(i)
          hash |= 0
        }
        hash = Math.abs(hash)
        return '#' + hash.toString(16).substr(0, 6)
      }
    }
  }
</script>

<style scoped>
  .avatar {
    display: inline-block;
    background-color: black;
    color: white;
    width: 48px;
    height: 48px;
    font-size: 12px;
    border-radius: 50%;
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    background-image: none;
  }
  .avatar table {
    width: 100%;
    height: 100%;
    text-align: center;
    vertical-align: middle;
    margin: 0;
    padding: 0;

  }
  .avatar img {
    width: 100%;
    overflow: hidden;
  }
</style>

