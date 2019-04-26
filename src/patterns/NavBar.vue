<template>
  <component :is="type" :class="['nav', alignItems]">
    <a
      v-for="(item, index) in navItems"
      :key="index"
      :href="item.href"
      :class="{ active: localActive === item.component }"
      v-html="item.name"
    />
  </component>
</template>

<script>
/**
 * Used as main page navigation in templates.
 */
export default {
  name: "NavBar",
  status: "ready",
  release: "1.0.0",
  model: {
    prop: "active",
  },
  props: {
    /**
     * The html element name used for the nav bar.
     */
    type: {
      type: String,
      default: "nav",
    },
    /**
     * State which tab is active when initiated (using name of the component). If <codenull</code>, assumes no active component
     */
    active: {
      type: String,
      defaut: "null",
    },
    /**
     * Menu items to be displayed on the nav bar.
     */
    navItems: {
      required: true,
      type: Array,
    },
    /**
     * Determines if items should align <code>left</code>, <code>center</code> or <code>right</code>.
     */
    alignItems: {
      type: String,
      default: "center",
    },
  },
  computed: {
    localActive: {
      get() {
        return this.active
      },
      set(val) {
        this.$emit("input", val)
      },
    },
  },
}
</script>

<style lang="scss" scoped>
// Design Tokens with local scope
$color-nav-link: $color-asphalt;
$color-nav-link-active: $color-vermilion-darker;

.nav {
  @include stack-space($space-m);
  font-family: $font-heading;
  font-size: $size-m;
  line-height: $line-height-m;
  color: $color-white;
  width: 100%;
  @media #{$media-query-l} {
    // This is how you’d use design tokens with media queries
  }
  a {
    color: $color-nav-link;
    padding: $space-xxs 0;
    margin: 0 $space-s;
    text-decoration: none;
    display: inline-block;
    &:hover {
      border-bottom: 2px solid $color-nav-link;
    }
    &.active {
      border-bottom: 2px solid $color-nav-link;
      color: $color-nav-link;
    }
  }
}

.left {
  text-align: left;
}

.center {
  text-align: center;
}

.right {
  text-align: right;
}
</style>

<docs>
  ```jsx
  <NavBar active="Dashboard" :navItems="[
    {name: 'Dashboard', component: 'Dashboard', href: '/#/'},
    {name: 'Posts', component: 'Posts', href: '/#/'},
    {name: 'Users', component: 'Users', href: '/#/'},
    {name: 'Settings', component: 'Settings', href: '/#/'}
  ]"/>
  ```
</docs>
