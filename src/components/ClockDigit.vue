<template>
  <div class="digit">
    <div class="line line-top" :class="{ active: activeLine(top) }"></div>
    <div class="line line-bottom" :class="{ active: activeLine(bottom) }"></div>
    <div
      class="line line-top-left"
      :class="{ active: activeLine(topLeft) }"
    ></div>
    <div
      class="line line-top-right"
      :class="{ active: activeLine(topRight) }"
    ></div>
    <div class="line line-center" :class="{ active: activeLine(center) }"></div>
    <div
      class="line line-bottom-left"
      :class="{ active: activeLine(bottomLeft) }"
    ></div>
    <div
      class="line line-bottom-right"
      :class="{ active: activeLine(bottomRight) }"
    ></div>
  </div>
</template>

<script>
export default {
  props: ["digit"],
  data() {
    return {
      top: [0, 2, 3, 5, 6, 7, 8, 9],
      bottom: [0, 2, 3, 5, 6, 8, 9],
      topLeft: [0, 4, 5, 6, 8, 9],
      topRight: [0, 1, 2, 3, 4, 7, 8, 9],
      center: [2, 3, 4, 5, 6, 8, 9],
      bottomLeft: [0, 2, 6, 8],
      bottomRight: [0, 1, 3, 4, 5, 6, 7, 8, 9],
    };
  },
  methods: {
    activeLine(lineDigits) {
      return lineDigits.includes(this.digit);
    },
  },
};
</script>

<style>
.digit {
  margin: 10px 30px;
  height: var(--digit-h);
  width: var(--digit-w);
  position: relative;
}

.digit .line {
  width: 100%;
  height: var(--digit-line-w);
  background-color: var(--primary);
  position: absolute;
  border-radius: 10px;

  opacity: 0;
  transition: opacity 200ms;
}

.digit .line.active {
  opacity: 1;
  transition: opacity 200ms;
}

.digit .line.line-top {
  top: calc(var(--digit-line-w) * -1);
}

.digit .line.line-bottom {
  bottom: calc(var(--digit-line-w) * -1);
}

.digit .line.line-top-left {
  top: calc(var(--digit-line-w) * -1);
  left: calc(var(--digit-line-w) * -1);
  transform: rotate(90deg)
    translate(calc(var(--digit-w) / 2), calc(var(--digit-w) / 2));
}

.digit .line.line-top-right {
  top: calc(var(--digit-line-w) * -1);
  right: calc(var(--digit-line-w) * -1);
  transform: rotate(90deg)
    translate(calc(var(--digit-w) / 2), calc(var(--digit-w) / -2));
}

.digit .line.line-center {
  top: calc(var(--digit-line-w) / -2);
  transform: translateY(calc(var(--digit-h) / 2));
}

.digit .line.line-bottom-left {
  bottom: calc(var(--digit-line-w) * -1);
  left: calc(var(--digit-line-w) * -1);
  transform: rotate(90deg)
    translate(calc(var(--digit-w) / -2), calc(var(--digit-w) / 2));
}

.digit .line.line-bottom-right {
  bottom: calc(var(--digit-line-w) * -1);
  right: calc(var(--digit-line-w) * -1);
  transform: rotate(90deg)
    translate(calc(var(--digit-w) / -2), calc(var(--digit-w) / -2));
}
</style>