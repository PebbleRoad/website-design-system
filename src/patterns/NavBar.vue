<template>
  <component :is="type" :class="['nav', alignItems]">
    <div class="navlinks">
      <a
        v-for="(item, index) in navItems"
        :key="index"
        :href="item.href"
        :class="[, { active: localActive === item.component }]"
        v-html="item.name"
      />
    </div>
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
      default: "right",
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
$color-nav-link: $color-asphalt;
$color-nav-link-active: $color-vermilion-darker;

.nav {
  @include stack-space($space-m);
  font-family: $font-heading;
  font-size: $size-xs;
  line-height: $line-height-m;
  color: $color-white;
  width: 100%;
  display: flex;

  &.left {
    justify-content: flex-start;
  }

  &.center {
    justify-content: center;
  }

  &.right {
    justify-content: flex-end;
  }

  @media #{$media-query-m} {
    font-size: $size-s;
  }
}

.navlinks {
  display: inline;

  a {
    display: block;
    color: $color-nav-link;
    padding: $space-xxxs/2 0;
    margin: 0 $space-xs;
    text-decoration: none;
    display: inline-block;
    &:hover {
      border-bottom: 2px solid $color-nav-link;
      transition: all 0.1s ease;
    }
    &.active {
      border-bottom: 2px solid $color-nav-link;
      color: $color-nav-link;
    }
    &.focus {
      border: 2px solid $color-granite;
    }

    @media #{$media-query-m} {
      margin: 0 $space-s;
    }
  }
}
</style>

<docs>
  ```jsx
  <div>
    <NavBar active="Dashboard" :navItems="[
      {name: 'Dashboard', component: 'Dashboard', href: '/#/'},
      {name: 'Posts', component: 'Posts', href: '/#/'},
      {name: 'Users', component: 'Users', href: '/#/'},
      {name: 'Settings', component: 'Settings', href: '/#/'}
    ]"/>
  <Paragraph>
    Design isn’t just about the look and feel. Design is how it works, and we believe the best way to focus on this is to work as close to the end result as possible. That’s why we start all our projects with simple sketches, and quickly transition into designing working prototypes in code. This is done by the same designers who started the work, which ensures that our original design intent is carried all the way to the end product.
  </Paragraph>
  </div>
  ```
</docs>
