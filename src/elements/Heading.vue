<template>
  <component :is="level" class="heading">
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
  },
}
</script>

<style lang="scss" scoped>
.heading {
  @include reset;
  font-family: $font-heading;
}
h1 {
  @include stack-space($space-m);
  letter-spacing: $spacing-xs;
  font-size: $size-2xl;
  line-height: $line-height-2xl;
  font-weight: $weight-bold;
  @media #{$media-query-m} {
    font-size: $size-3xl;
    line-height: $line-height-3xl;
  }
}
h2 {
  @include stack-space($space-m);
  letter-spacing: $spacing-s;
  font-size: $size-xl;
  line-height: $line-height-xl;
  font-weight: $weight-bold;
}
h3 {
  @include stack-space($space-s);
  font-size: $size-l;
  line-height: $line-height-l;
  font-weight: $weight-bold;
}
h4 {
  @include stack-space($space-s);
  font-size: $size-m;
  line-height: $line-height-m;
  font-weight: $weight-bold;
}
</style>

<docs>
  ```jsx
  <div>
    <Heading>The quick brown fox</Heading>
    <Heading level="h2">The quick brown fox</Heading>
    <Heading level="h3">The quick brown fox</Heading>
    <Heading level="h4">The quick brown fox</Heading>
  </div>
  ```
</docs>
