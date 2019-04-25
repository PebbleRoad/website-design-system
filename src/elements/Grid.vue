<template>
  <component :is="type" :class="['grid', columns, spacing]">
    <slot />
  </component>
</template>

<script>
/**
 * This is an explanation of Grids
 */
export default {
  name: "Grid",
  status: "prototype",
  release: "1.0.0",
  props: {
    type: {
      type: String,
      default: "div",
      validator: value => value.match(/div|span/),
    },
    /** Specifies the number of columns, up to <code>four</code> */
    columns: {
      type: String,
      required: true,
      default: "one",
      validator: value => value.match(/(one|two|three|four)/),
    },
    /**
     * Specifies <code>grid-gap</code>, options <code>s</code>, <code>m</code> or <code>l</code>
     * */
    spacing: {
      type: String,
      default: null,
    },
  },
}
</script>

<style lang="scss" scoped>
.grid {
  display: grid;
  width: 100%;
  box-sizing: border-box;
}

.one {
  grid-template-columns: 1fr;
}

.two {
  grid-template-columns: 1fr 1fr;
}

.three {
  grid-template-columns: 1fr 1fr 1fr;
}

.four {
  grid-template-columns: 1fr 1fr 1fr 1fr;
}

.s {
  grid-gap: 8px;
}

.m {
  grid-gap: 16px;
}

.l {
  grid-gap: 24px;
}
</style>

<docs>
  ```jsx
  <div>
    <Grid columns="three" spacing="s">
      <div style="background-color:lightgray; text-align:center;">
        <TextStyle>grid 1</TextStyle>
      </div>
      <div style="background-color:lightgray; text-align:center;">
        <TextStyle>grid 2</TextStyle>
      </div>
      <div style="background-color:lightgray; text-align:center;">
        <TextStyle>grid 3</TextStyle>
      </div>
      <div style="background-color:lightgray; text-align:center;">
        <TextStyle>grid 4</TextStyle>
      </div>
    </Grid>
  </div>
  ```
</docs>
