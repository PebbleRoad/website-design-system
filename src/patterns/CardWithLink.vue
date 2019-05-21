<template>
  <component
    :is="type"
    :class="['card', { 'border--show': border === true }, { 'fix--height': fixedHeight === true }]"
  >
    <div :class="padding"><slot /></div>
  </component>
</template>

<script>
/** Card explanation */
export default {
  name: "CardWithLink",
  status: "prototype",
  release: "1.0.0",
  props: {
    /**
     * <code>div</code> or <code>span</code>
     * */
    type: {
      type: String,
      default: "div",
      validator: value => value.match(/div|span/),
    },
    /** Specifies the media URL */

    border: {
      type: Boolean,
      default: false,
    },
    /**
     * Specifies <code>grid-gap</code>, options <code>s</code>, <code>m</code> or <code>l</code>
     * */
    padding: {
      type: String,
      default: null,
    },
    /**
     * Fixes height of card to 255px
     * */
    fixedHeight: {
      type: Boolean,
      default: false,
    },
  },
}
</script>

<style lang="scss" scoped>
$card-height: 255px;

.card {
  @include reset;
  width: inherit;
  height: 100%;
  box-sizing: border-box;

  &.fix--height {
    height: $card-height;

    div {
      height: 100%;
      box-sizing: border-box;
    }
  }
}

.s {
  padding: $space-s;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.m {
  padding: $space-m;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.l {
  padding: $space-l;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.border--show {
  box-shadow: $shadow-s;
}
</style>

<docs>
  ```jsx
  <Grid columns="three" spacing="m">
    <CardWithLink border padding="s">
      <Paragraph>      
        <Paragraph variation="medium" bold>Lorem Ipsum</Paragraph>
        Lorem ipsum dolor sit amet, consectetur adipiscing elit.
      </Paragraph>
      <div style="height:20px;"><Link>LINK</Link></div>
    </CardWithLink> 

    <CardWithLink border padding="m">
      <Paragraph>      
        <Paragraph variation="medium" bold>Lorem Ipsum</Paragraph>
        Lorem ipsum dolor sit amet, consectetur adipiscing elit.
      </Paragraph>
      <div style="height:20px;"><Link>LINK</Link></div>
    </CardWithLink> 

    <CardWithLink border padding="l">
      <Paragraph>      
        <Paragraph variation="medium" bold>Lorem Ipsum</Paragraph>
        Lorem ipsum dolor sit amet, consectetur adipiscing elit.
      </Paragraph>
      <div style="height:20px;"><Link>LINK</Link></div>
    </CardWithLink> 

    <CardWithLink border fixedHeight padding="l">
      <div>
         <Paragraph>      
          <Paragraph variation="medium" bold>Lorem Ipsum</Paragraph>
          Lorem ipsum dolor sit amet, consectetur adipiscing elit.
        </Paragraph>
      </div>
      <div style="height:20px;"><Link>LINK</Link></div>
    </CardWithLink> 

    <CardWithLink border fixedHeight padding="l">
      <div>
        <Paragraph>      
          <Paragraph variation="medium" bold>Lorem Ipsum</Paragraph>
          Lorem ipsum dolor sit amet.
        </Paragraph>
      </div>
      <div style="height:20px;"><Link>LINK</Link></div>
    </CardWithLink> 
  </Grid>

  ```
  </docs>
