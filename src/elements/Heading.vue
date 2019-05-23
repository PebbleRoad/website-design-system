<template>
  <component :is="level" :class="['heading', { margin__bottom: marginBottom === true }]">
    <slot />
  </component>
</template>

<script>
/**
 * Headings are used as the titles of each major section of a page in the
 * interface. For example, templates generally use headings as their title.
 * Heading element provides an option to change the level of the heading.
 */
export default {
  name: "Heading",
  status: "prototype",
  release: "1.0.0",
  props: {
    /**
     * The heading level used for the heading.
     * `h1, h2, h3, h4, h5, h6`
     */
    level: {
      type: String,
      default: "h1",
      validator: value => {
        return value.match(/(h1|h2|h3|h4|h5|h6)/)
      },
    },
    marginBottom: {
      type: Boolean,
      default: false,
    },
  },
}
</script>

<style lang="scss" scoped>
.heading {
  @include reset;
  margin-bottom: $space-xs;
  font-family: $font-heading;
}

.margin__bottom {
  margin-bottom: $space-m;
  @media #{$media-query-m} {
    margin-bottom: $space-xl;
  }
}

h1 {
  letter-spacing: $spacing-xs;
  font-size: $size-2xl;
  line-height: $line-height-l;
  margin-bottom: $space-s;
  font-weight: $weight-bold;
  @media #{$media-query-m} {
    font-size: $size-3xl;
    line-height: $line-height-xl;
  }
}
h2 {
  letter-spacing: $spacing-s;
  font-size: $size-xl;
  line-height: $line-height-l;
  font-weight: $weight-bold;
}
h3 {
  font-size: $size-l;
  line-height: $line-height-l;
  font-weight: $weight-bold;
}
h4 {
  font-size: $size-m;
  line-height: $line-height-m;
  font-weight: $weight-bold;
}
</style>

<docs>
  ```jsx
  <div>
    <Heading>The quick brown fox</Heading>
    <Heading level="h2" marginBottom>The quick brown fox</Heading>
    <Heading level="h2">The quick brown fox</Heading>
    <Heading level="h3">The quick brown fox</Heading>
    <Heading level="h4">The quick brown fox</Heading>
  </div>
  ```
</docs>
