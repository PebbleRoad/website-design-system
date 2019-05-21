<template>
  <component :is="type" :class="['paragraph', variation, { 'bold--show': bold === true }]">
    <slot />
  </component>
</template>

<script>
export default {
  name: "Paragraph",
  status: "prototype",
  release: "3.5.0",
  props: {
    /**
     * The html element used for the text.
     * `p, span`
     */
    type: {
      type: String,
      default: "p",
      validator: value => {
        return value.match(/(p|span)/)
      },
    },
    /**
     * Style variation to give additional meaning.
     * `intro, small, medium, large`
     */
    variation: {
      type: String,
      default: "small",
      validator: value => {
        return value.match(/(medium|intro|large|small)/)
      },
    },
    bold: {
      type: Boolean,
      default: false,
    },
  },
}
</script>

<style lang="scss" scoped>
.paragraph {
  @include reset;
  @include stack-space($space-m);
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  transition: color 0.3s ease;
  font-family: $font-text;
  color: $color-asphalt;
  font-size: $size-s;
  line-height: $line-height-s;

  a {
    font-size: inherit;
    font-family: inherit;
    font-weight: inherit;
  }

  &.intro {
    font-size: 1.5rem;
    line-height: $line-height-m;
  }

  &.medium {
    font-size: $size-m;
    line-height: $line-height-m;
  }

  &.large {
    font-size: $size-l;
    line-height: $line-height-l;
  }

  &.bold--show {
    font-weight: $weight-bold;
  }
}
</style>

<docs>
  ```jsx
  <div>
    <Heading level="h1">Heading h1</Heading>
    <Heading level="h2">Heading h2</Heading>
    <Heading level="h3">Heading h3</Heading>
    <br />    
    <Paragraph variation="large">
      Our <Link href="/#/Design%20Principles">core belief</Link> is that the products we design should work across anything that can access the web.
    </Paragraph>
    <Paragraph variation="medium">
      Our <Link href="/#/Design%20Principles">core belief</Link> is that the products we design should work across anything that can access the web.
    </Paragraph>
    <Paragraph>
      Design isn’t just about the look and feel. Design is <Link href="https://viljamis.com/2017/design-tools-processes/">how it works</Link>, and we believe the best way to focus on this is to work as close to the end result as possible. That’s why we start all our projects with simple sketches, and quickly transition into designing working prototypes in code. This is done by the same designers who started the work, which ensures that our original design intent is carried all the way to the end product.
    </Paragraph>


    <Paragraph variation="intro">
      Our <Link href="/#/Design%20Principles">core belief</Link> is that the products we design should work across anything that can access the web.
    </Paragraph>
    
  </div>
  ```
</docs>
