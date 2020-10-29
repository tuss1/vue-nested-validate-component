<template>
  <div>
    {{uid}}
    <slot></slot>
  </div>
</template>

<script>
  export default {
    props: ['uid'],
    methods: {
      traverse_(arr) {
        arr.forEach(element => {
          if (element.componentInstance) {
            if (element.componentOptions.tag === this.$vnode.componentOptions.tag) {
              element.componentInstance.validate();
            } else {
              if (element.componentInstance.$slots['default'])
                this.traverse_(element.componentInstance.$slots['default'])
            }
          } else if (element.children) {
            this.traverse_(element.children)
          }
        });
      },
      validate() {
        console.log(`validate called at ${this.$props['uid']}`)

        if (this.$slots['default']) this.traverse_(this.$slots['default'])
      }
    },
  }
</script>