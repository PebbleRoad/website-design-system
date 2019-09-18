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
      validator: value => value.match(/(one|two|three|four|six)/),
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
  display: -ms-grid;
  display: grid;
  width: 100%;
  box-sizing: border-box;
  -webkit-box-sizing: border-box;
  -ms-grid-columns: 1fr;
  grid-template-columns: 1fr;
}

.one {
  -ms-grid-columns: 1fr;
  grid-template-columns: 1fr;
}

.two {
  @media #{$media-query-m} {
    -ms-grid-columns: 1fr 1fr;
    grid-template-columns: 1fr 1fr;
  }
  @media #{$media-query-l} {
    -ms-grid-columns: 1fr 1fr;
    grid-template-columns: 1fr 1fr;
  }
}

.three {
  @media #{$media-query-m} {
    -ms-grid-columns: 1fr 1fr;
    grid-template-columns: 1fr 1fr;
  }
  @media #{$media-query-l} {
    -ms-grid-columns: 1fr 1fr 1fr;
    grid-template-columns: 1fr 1fr 1fr;
  }
}

.four {
  @media #{$media-query-m} {
    -ms-grid-columns: 1fr 1fr;
    grid-template-columns: 1fr 1fr;
  }
  @media #{$media-query-l} {
    -ms-grid-columns: 1fr 1fr 1fr 1fr;
    grid-template-columns: 1fr 1fr 1fr 1fr;
  }
}

.six {
  @media #{$media-query-m} {
    -ms-grid-columns: 1fr 1fr 1fr;
    grid-template-columns: 1fr 1fr 1fr;
  }
  @media #{$media-query-l} {
    -ms-grid-columns: 1fr 1fr 1fr 1fr 1fr 1fr;
    grid-template-columns: 1fr 1fr 1fr 1fr 1fr 1fr;
  }
}

.s {
  grid-gap: $size-s;
}

.m {
  grid-gap: $size-m;
}

.l {
  grid-gap: $size-l;
}
</style>

<docs>
  ```jsx
  <div>
    <Grid columns="four" spacing="l">
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
