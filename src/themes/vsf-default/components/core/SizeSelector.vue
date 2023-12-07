<template>
  <button
    class="
      p0 bg-cl-primary brdr-1 brdr-cl-primary
      brdr-square h5 cl-tertiary size-selector
    "
    :class="{ active: isActive }"
    @click="$emit('change', variant)"
    :aria-label="$t('Select size {variant}', { variant: variant.label })"
  >
    {{ variant.label }}
  </button>
</template>

<script>
import filterMixin from 'theme/mixins/filterMixin.ts'

export default {
  mixins: [filterMixin]
}
</script>

<style lang="scss" scoped>
  @import '~theme/css/variables/colors';
  @import '~theme/css/helpers/functions/color';
  $color-active: color(secondary);
  $color-disabled: color(secondary, $colors-border);

  .size-selector {
    width: 38px;
    height: 18px;

    &:hover,
    &:focus {
      border-width: 2px;
    }

    &.active {
      border-color: #000;
    border-width: 2px;
    color: #FFF;
    background-color: #313131;
    }

    &:disabled {
      border-color: $color-disabled;
      color: $color-disabled;
      cursor: not-allowed;

      &:hover,
      &:after {
        border-width: 1px;
      }
    }
  }
</style>
