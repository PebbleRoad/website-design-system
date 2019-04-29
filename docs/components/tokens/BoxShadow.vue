<template>
  <div class="box-shadows">
    <div
      v-for="(prop, index) in tokens"
      :key="index"
      class="box-shadow"
      :class="prop.category"
      v-if="prop.category === 'box-shadow'"
    >
      <div class="swatch" :style="{ boxShadow: prop.value }" />
      <h3>{{ prop.name.replace(/_/g, " ").replace(/color/g, "") }}</h3>
      <span>
        <em>value:</em>
        {{ prop.value }}
      </span>
      <span>
        <em>SCSS:</em>
        ${{ prop.name.replace(/_/g, "-") }}
      </span>
    </div>
  </div>
</template>

<script>
import designTokens from "@/assets/tokens/tokens.raw.json"
import orderBy from "lodash/orderBy"

export default {
  name: "BoxShadow",
  methods: {
    orderData: function(data) {
      let byValue = orderBy(data, "category", "desc")
      let byCategoryAndName = orderBy(byValue, "category")
      return byCategoryAndName
    },
  },
  data() {
    return {
      tokens: this.orderData(designTokens.props),
    }
  },
}
</script>

<style lang="scss" scoped>
@import "../../docs.tokens.scss";

/* STYLES
--------------------------------------------- */

.box-shadows {
  margin-top: $space-l;
  display: block;
  width: 100%;
  @supports (display: grid) {
    display: grid;
    max-width: 1200px;
    align-content: stretch;
    justify-content: left;
    grid-template-columns:
      calc(20% - #{$space-m})
      calc(20% - #{$space-m})
      calc(20% - #{$space-m})
      calc(20% - #{$space-m})
      calc(20% - #{$space-m});
    grid-column-gap: $space-m;
    @media (max-width: 1300px) {
      grid-template-columns:
        calc(25% - #{$space-m})
        calc(25% - #{$space-m})
        calc(25% - #{$space-m})
        calc(25% - #{$space-m});
    }
    @media (max-width: 1100px) {
      grid-template-columns:
        calc(33.333% - #{$space-m})
        calc(33.333% - #{$space-m})
        calc(33.333% - #{$space-m});
    }
    @media (max-width: 900px) {
      grid-template-columns:
        calc(50% - #{$space-m})
        calc(50% - #{$space-m});
    }
    @media (max-width: 400px) {
      grid-template-columns: 100%;
    }
  }
}
.swatch {
  @include stack-space($space-s);
  border-bottom: 1px solid rgba(0, 0, 0, 0.08);
  height: $space-xxl;
  margin-left: -#{$space-s};
  margin-top: -#{$space-s};
  width: calc(100% + #{$space-l});
  float: left;
  background-color: $color-grey-light;
}
h3 {
  @include reset;
  @include stack-space($space-xs);
  text-transform: capitalize;
  line-height: 1.2;
  width: 100%;
  float: left;
}
.box-shadow {
  @include reset;
  @include inset-space($space-s);
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  margin-bottom: $space-m;
  box-shadow: 0 0 0 1px rgba(63, 63, 68, 0.05), 0 1px 3px 0 rgba(63, 63, 68, 0.15);
  font-size: $size-xs;
  font-family: $font-text;
  color: $color-grey-darker;
  border-radius: $radius-default;
  overflow: hidden;
  text-align: left;
  @supports (display: grid) {
    width: 100%;
    float: left;
  }
  @media (max-width: 400px) {
    margin-bottom: $space-m;
  }
  &:hover {
    span {
      color: $color-grey-darker;
      em {
        color: $color-grey-dark;
      }
    }
  }
  span {
    margin-bottom: $space-xs;
    line-height: 1.3;
    color: $color-grey-dark;
    font-size: $size-xs;
    width: 100%;
    float: left;
    em {
      user-select: none;
      font-style: normal;
    }
  }
}
</style>

<docs>
  ```jsx
  <color/>
  ```
</docs>
