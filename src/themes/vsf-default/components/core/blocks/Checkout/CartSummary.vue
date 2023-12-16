<template>
  <div class="checkout_summary_dv">
    <div class="brdr-cl-primary pb60 order-hd">
      <div class="item-hd-sec">
        <h3 class="cl-accent ml30 mt50 summary-title">
        {{ $t('Item') }}
      </h3>
      <h3 class="cl-accent ml30 mt50 summary-title">
        {{ $t('Price') }}
      </h3>
      </div>
      <div v-if="productsInCart && productsInCart.length" class="tp-brd">
        <product class="btm-brd" v-for="product in productsInCart" :key="product.server_item_id || product.id" :product="product" />
      </div>
      
      <div v-if="productsInCart && productsInCart.length" class="checkout bg-cl-secondary pt10 serif cl-accent grd-total">
        <div class="brd-btm-grd">
        <div v-for="(segment, index) in totals" :key="index" class="row pt15 pb20 pl30 pr55 border-btm" v-if="segment.code !== 'grand_total'">
          <div class="col-xs cl-accent sub-tlt">
            {{ segment.title }}
          </div>
          <div v-if="segment.value != null" class="col-xs align-right cl-accent h4">
            {{ segment.value | price(storeView) }}
          </div>
        </div>

        <div class="row pt20 pb20 pl30 pr55 weight-400 h3 grd-sec" v-for="(segment, index) in totals" :key="index" v-if="segment.code === 'grand_total'">
          <div class="col-xs ">
            {{ segment.title }}
          </div>
          <div class="col-xs align-right">
            {{ segment.value | price(storeView) }}
          </div>
        </div>
      </div>
      </div>
    </div>
    <!-- <div class="py50 px25">
      <h4 class="h3 m0">
        {{ $t('Safety') }}
      </h4>
      <p class="cl-tertiary lh20">
        Lorem ipsum dolor sit amet, consectetur adipiscing elit.
        Nullam sed tempor lorem. Vivamus volutpat eros id est semper accumsan.
      </p>
      <h4 class="h3 mb0" v-if="!isVirtualCart">
        {{ $t('Shipping') }}
      </h4>
      <p class="cl-tertiary lh20" v-if="!isVirtualCart">
        Lorem ipsum dolor sit amet, consectetur adipiscing elit.
        Nullam sed tempor lorem. Vivamus volutpat eros id est semper accumsan.
      </p>
      <h4 class="h3 mb0">
        {{ $t('Returns') }}
      </h4>
      <p class="cl-tertiary lh20">
        Lorem ipsum dolor sit amet, consectetur adipiscing elit.
        Nullam sed tempor lorem. Vivamus volutpat eros id est semper accumsan.
      </p>
    </div> -->
  </div>
</template>

<script>
import { CartSummary } from '@vue-storefront/core/modules/checkout/components/CartSummary'
import { currentStoreView } from '@vue-storefront/core/lib/multistore'
import Product from './Product'

export default {
  components: {
    Product
  },
  computed: {
    storeView () {
      return currentStoreView()
    }
  },
  mixins: [CartSummary]
}
</script>

<style lang="scss" scoped>
  .summary-title {
    @media (max-width: 767px) {
      margin-left: 0;
    }
  }

  .checkout_summary_dv {
    width: 100%;
  }
  .order-hd{
    padding-top: 100px;
  }
  .item-hd-sec {
    display: flex;
    align-items: flex-start;
    gap: 50%;
    justify-content: center;
  }
  .summary-title {
    font-size: 22px;
    font-weight: 400;
    color: #302A2A;
  }
  .btm-brd {
    border-bottom: 1px solid #FFF;
    padding: 50px 0px;
    gap: 20px;
  }
  .tp-brd {
    padding: 0 30px;
  }
  .sub-tlt {
    font-size: 22px;
  }
  .checkout.bg-cl-secondary.pt10.serif.cl-accent.grd-total {
    width: 65%;
    float: right;
    padding-top: 50px;
  }
  .grd-sec {
    padding-bottom: 55px;
  } 
  @media only screen and (min-device-width: 768px) and (max-device-width: 991px) {
    .sub-tlt {
    font-size: 19px;
  }
  .grd-total {
    width: 85% !important;
  }
}
</style>
