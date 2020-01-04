<template>
  <div
    :class="classObj"
    class="app-wrapper">
    <div class="main-container">
      <navbar />
      <app-main />
    </div>
  </div>
</template>

<script lang="ts">
import { Component } from 'vue-property-decorator'
import { mixins } from 'vue-class-component'
import { DeviceType, AppModule } from '@/store/modules/app'
import { AppMain, Navbar} from './components'
import ResizeMixin from './mixin/resize'

@Component({
  name: 'Layout',
  components: {
    AppMain,
    Navbar,
  }
})
export default class extends mixins(ResizeMixin) {
  get classObj() {
    return {
      mobile: this.device === DeviceType.Mobile
    }
  }
}
</script>

<style lang="scss" scoped>
.app-wrapper {
  @include clearfix;
  position: relative;
  height: 100%;
  width: 100%;
}

.drawer-bg {
  background: #000;
  opacity: 0.3;
  width: 100%;
  top: 0;
  height: 100%;
  position: absolute;
  z-index: 999;
}

.main-container {
  min-height: 100%;
  position: relative;
}

/* for mobile response 适配移动端 */
.mobile {
  .main-container {
    margin-left: 0px;
  }

}

</style>
