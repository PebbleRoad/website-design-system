<template>
  <component
    :is="spacing"
    :class="['tag', spacing, { invert: invert === true }]"
    v-bind:style="{ 'background-color': color }"
  >
    <slot />
  </component>
</template>

<script>
/**
 * Tags
 */
export default {
  name: "Tag",
  status: "prototype",
  release: "1.0.0",
  props: {
    /**
     * The spacing used for the tag.
     * `small, medium`
     */
    spacing: {
      type: String,
      default: "small",
      validator: value => {
        return value.match(/(small|medium)/)
      },
    },
    invert: {
      type: Boolean,
      default: false,
    },
    fill: {
      type: String,
      default: null,
    },
  },
  data() {
    return {
      color: this.fill,
    }
  },
}
</script>

<style lang="scss" scoped>
.tag {
  @include reset;
  @include stack-space($space-m);
  @include inline-space($space-xs);
  font-family: $font-text;
  color: $color-asphalt;
  border: 1px solid $color-asphalt;
  border-radius: 500px;
}

.small {
  padding: $space-xxxs $space-xxs;
  font-size: $size-xxs;
}

.medium {
  padding: $space-xxs $space-xs;
  font-size: $size-xs;
}

.invert {
  border: 1px solid $color-grey-light;
  color: $color-grey-light;
}
</style>

<docs>
  ```jsx
  <div>
    <Tag>Default tag</Tag>
    <Tag fill="#d7e4eb">Default tag</Tag>
    <Tag invert fill="#a79a93">Inverted tag</Tag>
    <Tag spacing="medium">Medium tag</Tag>
  </div>
  ```
</docs>
