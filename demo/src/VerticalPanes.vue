<template>
<multipane class="vertical-panes" layout="vertical" @resize="paneResize" @resizestart='paneResizeStart' @resizestop='paneResizeStop'>
  <div class="pane" :style="{ minWidth: '100px', width: '150px', maxWidth: '200px' }">
    <div>
      <h6 class="title is-6">Pane 1</h6>
      <p class="subtitle is-6">Fixed width.</p>
      <p>
        <small>
          <strong>Configured with:</strong><br/>
          minWidth: 100px<br/>
          width: 150px<br/>
          maxWidth: 200px<br/>
          start resizing: {{ startResizing }}<br/>
          stop resizing: {{ stopResizing }}<br/>
          resizing: {{ resizing }}<br/>
        </small>
      </p>
    </div>
  </div>
  <multipane-resizer></multipane-resizer>
  <div class="pane" :style="{ width: '25%', maxWidth: '50%' }">
    <div>
      <h6 class="title is-6">Pane 2</h6>
      <p class="subtitle is-6">Fluid width.</p>
      <p>
        <small>
          <strong>Configured with:</strong><br/>
          width: 25%<br/>
          maxWidth: 50%<br/>
          start resizing: {{ startResizing }}<br/>
          stop resizing: {{ stopResizing }}<br/>
          resizing: {{ resizing }}<br/>
        </small>
      </p>
    </div>
  </div>
  <multipane-resizer></multipane-resizer>
  <div class="pane" :style="{ flexGrow: 1 }">
    <div>
      <h6 class="title is-6">Pane 3</h6>
      <p class="subtitle is-6">Takes remaining available space.</p>

      <p>
        <small>
          <strong>Configured with:</strong><br/>
          flex-grow: 1<br/>
          start resizing: {{ startResizing }}<br/>
          stop resizing: {{ stopResizing }}<br/>
          resizing: {{ resizing }}<br/>
        </small>
      </p>
    </div>
  </div>
</multipane>
</template>

<script>
import { Multipane, MultipaneResizer } from '@/src';
const data = {
  startResizing: false,
  stopResizing: true,
  resizing: false
}
export default {

  data() {
    return data;
  },

  methods: {
    paneResizeStart() {
      this.startResizing = true;
      this.stopResizing = false;
    },

    paneResizeStop() {
      this.stopResizing = true;
      this.startResizing = false;
      this.resizing = false;
    },

    paneResize() {
      this.resizing = true;
    }
  },

  components: {
    Multipane,
    MultipaneResizer,
  },
};
</script>

<style scoped>
.vertical-panes {
  width: 100%;
  height: 400px;
  border: 1px solid #ccc;
}

.vertical-panes > .pane {
  text-align: left;
  padding: 15px;
  overflow: hidden;
  background: #eee;
}

.vertical-panes > .pane ~ .pane {
  border-left: 1px solid #ccc;
}
</style>
