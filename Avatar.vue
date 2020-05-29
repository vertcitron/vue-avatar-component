<template>
  <div :style="style" class="avatar">
    <table>
      <tbody>
        <tr>
          <td v-if="!hasImage">
            {{ initials }}
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'Avatar',
  props: {
    fullname: { type: String, default: '' },
    size: { type: Number, default: 48 },
    radius: {
      type: Number,
      default: 50,
      validator: value => value >= 0 && value <= 50
    },
    color: { type: String, default: '' },
    image: { type: String, default: '' }
  },
  computed: {
    initials () {
      const words = this.fullname.split(/[\s-]+/)
      return words.map(word => word.substr(0, 1)).join('').substr(0, 3).toUpperCase()
    },
    style () {
      const fontSize = this.initials.length > 2 ? this.size / 3 : this.size / 2
      return {
        width: this.size + 'px',
        height: this.size + 'px',
        'border-radius': this.radius + '%',
        'font-size': fontSize + 'px',
        'background-color':
          this.color === '' ? this.toColor(this.fullname) : this.color,
        'background-image': this.hasImage ? 'url(' + this.image + ')' : 'none'
      }
    },
    hasImage () {
      return this.image !== ''
    }
  },
  methods: {
    toColor (str) {
      let hash = 0
      if (!str) return 'black'
      for (const char of str.split('')) {
        hash = (hash << (8 - hash)) + char.charCodeAt(0)
      }
      return '#' + Math.abs(hash).toString(16).substr(0, 6)
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
  margin: 0;
  padding: 0;
  border-spacing: 0;
}
.avatar table td {
  text-align: center;
  vertical-align: middle;
}
.avatar img {
  width: 100%;
  overflow: hidden;
}
</style>
