<template>
  <component :is="type" :href="href" :class="['link', state]">
    <slot />
  </component>
</template>

<script>
/**
 * Links
 */
export default {
  name: "Link",
  status: "prototype",
  release: "1.0.0",
  props: {
    /**
     * The html element name used for the link.
     */
    type: {
      type: String,
      default: "a",
    },
    /**
     * Manually trigger various states of the button.
     * `hover, active, focus`
     */
    state: {
      type: String,
      default: null,
      validator: value => {
        return value.match(/(hover|active|focus|disabled)/)
      },
    },
    href: {
      type: String,
      default: null,
    },
  },
}
</script>

<style lang="scss" scoped>
@import "../../docs/docs.tokens.scss";

.link {
  @include reset;
  font-family: $font-text;
  font-size: $size-s;
  color: $color-asphalt;
  text-decoration: none;
  cursor: pointer;
  border-bottom: 1px solid $color-vermilion;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  transition: all 0.2s ease;
  &:hover,
  &.hover {
    border-bottom: 1px solid $color-asphalt;
  }
  &:active,
  &.active {
    border-bottom: 1px solid $color-asphalt;
  }
  &:focus,
  &.focus {
    border: 1px solid $color-granite;
  }
  &:disabled,
  &.disabled {
    cursor: not-allowed;
    color: $color-grey;
    border-bottom: 1px solid $color-grey;
  }
}
</style>

<docs>
```jsx
<Paragraph variation="small">
  Lorem ipsum dolor sit amet, consectetur <Link href="#">adipiscing</Link> elit. Cras facilisis feugiat aliquam.   
</Paragraph>

<div>
  <Link state="hover" href="#" style="margin-right: 20px;">:hover</Link>
  <Link state="active" href="#" style="margin-right: 20px;">:active</Link>
  <Link state="focus" href="#" style="margin-right: 20px;">:focus</Link>
  <Link state="disabled" href="#" style="margin-right: 20px;">:disabled</Link>
</div>
```
</docs>
