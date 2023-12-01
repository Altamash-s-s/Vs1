<template>
  <div id="product" >

    <storypopup v-if="showstorypopup" @close-popup="showstorypopup = false" />

    <video class="product-video" autoplay muted loop>
      <source :src="getCurrentProduct.product_video" type="video/mp4">
    </video>  
    <section class="bg-cl-secondary px20 product-top-section">
      <div class="container product_container">
        <section class="row m0">
          <div class="col-xs-12 col-md-6 center-xs middle-xs image img_slider_col">
            <product-gallery
              :offline="getOfflineImage"
              :gallery="getProductGallery"
              :configuration="getCurrentProductConfiguration"
              :product="getCurrentProduct"
              :prd_video="getCurrentProduct.product_closeup_video"
            />
          </div>
          <div class="col-xs-12 col-md-5 data prd_detail_col">

            <div class="prd_dtls_inner">
              <!-- <breadcrumbs
                class="pt40 pb20 hidden-xs"
              /> -->
              <h1
                class="mb20 mt0 cl-mine-shaft product-name"
                data-testid="productName"
              >
                {{ getCurrentProduct.name | htmlDecode }}
                <web-share
                  :title="getCurrentProduct.name | htmlDecode"
                  text="Check this product!"
                  class="web-share"
                />

                <AddToWishlist 
                  :product="getCurrentProduct" 
                  class="wishlist_cstm"  
                />

              </h1>
              
              <div
                class="mb20 uppercase cl-secondary"
                :content="getCurrentProduct.sku"
              >
                {{ $t('SKU: {sku}', { sku: getCurrentProduct.sku }) }}

               <!-- <div class="zaid" v-html="getCurrentProduct.size_guide"></div>  -->
              </div>
              <div>
                <product-price
                  class="mb40 price-cstm"
                  v-if="getCurrentProduct.type_id !== 'grouped'"
                  :product="getCurrentProduct"
                  :custom-options="getCurrentCustomOptions"
                />
                <div class="short-description" v-html="getCurrentProduct.short_description"> </div>
                <div class="cl-primary variants" v-if="getCurrentProduct.type_id =='configurable'">
                  <div
                    class="error"
                    v-if="getCurrentProduct.errors && Object.keys(getCurrentProduct.errors).length > 0"
                  >
                    {{ getCurrentProduct.errors | formatProductMessages }}
                  </div>
                  <div class="h5" v-for="option in getProductOptions" :key="option.id">
                    <div class="variants-label" data-testid="variantsLabel">
                      {{ option.label === 'Color' ? 'Color : -' : (option.label === 'Size' ? 'Size : -' : option.label) }}
                      <span
                        class="weight-700"
                      >{{ getOptionLabel(option) }}</span>
                    </div>
                    <div class="row top-xs m0 pt15 pb40 variants-wrapper">
                      <div v-if="option.label == 'Color'" class="color-bt-border prd_color">
                        <color-selector
                          v-for="filter in getAvailableFilters[option.attribute_code]"
                          :key="filter.id"
                          :variant="filter"
                          :selected-filters="getSelectedFilters"
                          @change="changeFilter"
                          class='color_button'
                        />
                      </div>
                      <div class="sizes" v-else-if="option.label == 'Size'">
                        <size-selector
                          class="mr10 mb10"
                          v-for="filter in getAvailableFilters[option.attribute_code]"
                          :key="filter.id"
                          :variant="filter"
                          :selected-filters="getSelectedFilters"
                          @change="changeFilter"
                        />
                      </div>
                      <div :class="option.attribute_code" v-else>
                        <generic-selector
                          class="mr10 mb10"
                          v-for="filter in getAvailableFilters[option.attribute_code]"
                          :key="filter.id"
                          :variant="filter"
                          :selected-filters="getSelectedFilters"
                          @change="changeFilter"
                        />
                      </div>
                      <span
                        v-if="option.label == 'Size'"
                        @click="openSizeGuide"
                        class="p0 ml30 inline-flex middle-xs no-underline h5 action size-guide pointer cl-secondary"
                      >
                        <i class="pr5 material-icons">accessibility</i>
                        <span>{{ $t('Size guide') }}</span>
                      </span>
                    </div>
                  </div>
                </div>
              </div>
              <product-links
                v-if="getCurrentProduct.type_id =='grouped'"
                :products="getCurrentProduct.product_links"
              />
              <product-bundle-options
                v-if="getCurrentProduct.bundle_options && getCurrentProduct.bundle_options.length > 0"
                :product="getCurrentProduct"
              />
              <product-custom-options
                v-else-if="getCurrentProduct.custom_options && getCurrentProduct.custom_options.length > 0"
                :product="getCurrentProduct"
              />
              <!-- <product-quantity
                class="row m0 mb35"
                v-if="getCurrentProduct.type_id !== 'grouped' && getCurrentProduct.type_id !== 'bundle'"
                v-model="getCurrentProduct.qty"
                :max-quantity="maxQuantity"
                :loading="isStockInfoLoading"
                :is-simple-or-configurable="isSimpleOrConfigurable"
                :show-quantity="manageQuantity"
                :check-max-quantity="manageQuantity"
                @error="handleQuantityError"
              /> -->
              <div class="row m0">
                <add-to-cart
                  :product="getCurrentProduct"
                  :disabled="isAddToCartDisabled"
                  class="col-xs-12 col-sm-4 col-md-6"
                />
              </div>

              <!-- <div class="popup-story">
                <button class="care-btn" @click="showstorypopup = true">Read Story</button>
              </div> -->

              <button id="story_btn">Read Story</button>

              <div id="story_overlay"></div>
              <div id="story_container">
                  <button class="popup-cancel" id="close-btn">&#10005;</button>
                  <div v-html="getCurrentProduct.product_story"></div> 
              </div>
          
              <!-- <div class="row py40 add-to-buttons">
              <div class="col-xs-6 col-sm-3 col-md-6">
                <AddToWishlist :product="getCurrentProduct" />
              </div>
              <div class="col-xs-6 col-sm-3 col-md-6">
                <AddToCompare :product="getCurrentProduct" />
              </div>
            </div> -->
            </div>          
          </div>

        </section>
      </div>
    </section>

    <section class="container px15 pt50 pb35 cl-accent details prd_tab_section">

        <div class="tab-navigation">
          <button @click="showTab('productDetailsTab')">Product Details</button>
          <button @click="showTab('careTab')">Care</button>
          <button @click="showTab('productCareTab')">Product Care</button>
        </div>

        <!-- Tab content -->
        <div class="tab-content active" id="productDetailsTab">
          <h2 class="h3 m0 mb10 serif lh20 details-title">Product Details</h2>
          <p class="care_description lh30 h5" v-html="getCurrentProduct.description"></p>
        </div>

        <div class="tab-content" id="careTab">
          <h2 class="h3 m0 mb10 serif lh20 details-title">Care</h2>
          <p class="care_description lh30 h5" >{{ getCurrentProduct.care }}</p>
        </div>

        <div class="tab-content" id="productCareTab">
          <h2 class="h3 m0 mb10 serif lh20 details-title">Product Care</h2>
          <div class="care_description">
            <div class="flex-dsc" v-html="getCurrentProduct.product_care">
            </div>
          </div>
        </div>
    </section>

    <!-- <lazy-hydrate when-idle>
      <reviews
        :product-name="getCurrentProduct.name"
        :product-id="getCurrentProduct.id"
        v-show="isOnline"
        :product="getCurrentProduct"
      />
    </lazy-hydrate> -->


    <!-- <lazy-hydrate when-idle>
      <related-products type="upsell" :heading="$t('We found other products you might like')" />
    </lazy-hydrate> -->
    <!-- <lazy-hydrate when-idle>
      <promoted-offers single-banner />
    </lazy-hydrate> -->
    <lazy-hydrate when-idle>
      <related-products type="related" />
    </lazy-hydrate>
    <SizeGuide :size_chart="getCurrentProduct.size_guide" />

    
    <script v-html="getJsonLd" type="application/ld+json" />
  </div>
</template>

<script>
import i18n from '@vue-storefront/i18n'
import VueOfflineMixin from 'vue-offline/mixin'
import config from 'config'
import RelatedProducts from 'theme/components/core/blocks/Product/Related.vue'
import Reviews from 'theme/components/core/blocks/Reviews/Reviews.vue'
import AddToCart from 'theme/components/core/AddToCart.vue'
import GenericSelector from 'theme/components/core/GenericSelector'
import ColorSelector from 'theme/components/core/ColorSelector.vue'
import SizeSelector from 'theme/components/core/SizeSelector.vue'
import Breadcrumbs from 'theme/components/core/Breadcrumbs.vue'
import ProductAttribute from 'theme/components/core/ProductAttribute.vue'
import ProductQuantity from 'theme/components/core/ProductQuantity.vue'
import ProductLinks from 'theme/components/core/ProductLinks.vue'
import ProductCustomOptions from 'theme/components/core/ProductCustomOptions.vue'
import ProductBundleOptions from 'theme/components/core/ProductBundleOptions.vue'
import ProductGallery from 'theme/components/core/ProductGallery'
import Spinner from 'theme/components/core/Spinner'
import PromotedOffers from 'theme/components/theme/blocks/PromotedOffers/PromotedOffers'
import focusClean from 'theme/components/theme/directives/focusClean'
import WebShare from 'theme/components/theme/WebShare'
import BaseInputNumber from 'theme/components/core/blocks/Form/BaseInputNumber'
import SizeGuide from 'theme/components/core/blocks/Product/SizeGuide'
import AddToWishlist from 'theme/components/core/blocks/Wishlist/AddToWishlist'
import AddToCompare from 'theme/components/core/blocks/Compare/AddToCompare'
import { mapGetters } from 'vuex'
import LazyHydrate from 'vue-lazy-hydration'
import { ProductOption } from '@vue-storefront/core/modules/catalog/components/ProductOption.ts'
import { getAvailableFiltersByProduct, getSelectedFiltersByProduct } from '@vue-storefront/core/modules/catalog/helpers/filters'
import { isOptionAvailableAsync } from '@vue-storefront/core/modules/catalog/helpers/index'
import { localizedRoute, currentStoreView } from '@vue-storefront/core/lib/multistore'
import { htmlDecode } from '@vue-storefront/core/filters'
import { ReviewModule } from '@vue-storefront/core/modules/review'
import { RecentlyViewedModule } from '@vue-storefront/core/modules/recently-viewed'
import { registerModule, isModuleRegistered } from '@vue-storefront/core/lib/modules'
import { onlineHelper, isServer, productJsonLd } from '@vue-storefront/core/helpers'
import { catalogHooksExecutors } from '@vue-storefront/core/modules/catalog-next/hooks'
import ProductPrice from 'theme/components/core/ProductPrice.vue'
import { doPlatformPricesSync } from '@vue-storefront/core/modules/catalog/helpers'
import { filterChangedProduct } from '@vue-storefront/core/modules/catalog/events'

import storypopup from './storypopup.vue'

export default {
  components: {
    AddToCart,
    AddToCompare,
    AddToWishlist,
    Breadcrumbs,
    ColorSelector,
    GenericSelector,
    ProductAttribute,
    ProductBundleOptions,
    ProductCustomOptions,
    ProductGallery,
    ProductLinks,
    PromotedOffers,
    RelatedProducts,
    Reviews,
    SizeSelector,
    WebShare,
    SizeGuide,
    LazyHydrate,
    ProductQuantity,
    ProductPrice,
    storypopup
  },
  mixins: [ProductOption],
  directives: { focusClean },
  beforeCreate () {
    registerModule(ReviewModule)
    registerModule(RecentlyViewedModule)
  },
  data () {
    return {
      detailsOpen: false,
      maxQuantity: 0,
      quantityError: false,
      isStockInfoLoading: false,
      hasAttributesLoaded: false,
      manageQuantity: true,
      showstorypopup: false,
    }
  },
  computed: {
    ...mapGetters({
      getCurrentCategory: 'category-next/getCurrentCategory',
      getCurrentProduct: 'product/getCurrentProduct',
      getProductGallery: 'product/getProductGallery',
      getCurrentProductConfiguration: 'product/getCurrentProductConfiguration',
      attributesByCode: 'attribute/attributeListByCode',
      getCurrentCustomOptions: 'product/getCurrentCustomOptions'
    }),
    getOptionLabel () {
      return (option) => {
        const configName = option.attribute_code ? option.attribute_code : option.label.toLowerCase()
        return this.getCurrentProductConfiguration[configName] ? this.getCurrentProductConfiguration[configName].label : configName
      }
    },
    isOnline (value) {
      return onlineHelper.isOnline
    },
    getProductOptions () {
      if (
        this.getCurrentProduct.errors &&
        Object.keys(this.getCurrentProduct.errors).length &&
        Object.keys(this.getCurrentProductConfiguration).length
      ) {
        return []
      }
      return this.getCurrentProduct.configurable_options
    },
    getOfflineImage () {
      return {
        src: this.getThumbnail(this.getCurrentProduct.image, config.products.thumbnails.width, config.products.thumbnails.height),
        error: this.getThumbnail(this.getCurrentProduct.image, config.products.thumbnails.width, config.products.thumbnails.height),
        loading: this.getThumbnail(this.getCurrentProduct.image, config.products.thumbnails.width, config.products.thumbnails.height)
      }
    },
    getCustomAttributes () {
      return Object.values(this.attributesByCode || [])
        .filter(
          a => a.is_visible && a.is_user_defined && (parseInt(a.is_visible_on_front) || a.is_visible_on_front === true) && this.getCurrentProduct[a.attribute_code]
        )
        .sort((a, b) => { return a.attribute_id > b.attribute_id })
    },
    getAvailableFilters () {
      return getAvailableFiltersByProduct(this.getCurrentProduct)
    },
    getSelectedFilters () {
      return getSelectedFiltersByProduct(this.getCurrentProduct, this.getCurrentProductConfiguration)
    },
    isSimpleOrConfigurable () {
      return ['simple', 'configurable'].includes(this.getCurrentProduct.type_id)
    },
    isAddToCartDisabled () {
      if (this.quantityError || this.isStockInfoLoading) {
        return false
      }

      return this.isOnline && !this.maxQuantity && this.manageQuantity && this.isSimpleOrConfigurable
    },
    storeView () {
      return currentStoreView()
    },
    getJsonLd () {
      return productJsonLd(this.getCurrentProduct, this.getCurrentProductConfiguration.color && this.getCurrentProductConfiguration.color.label, this.$store.state.storeView.i18n.currencyCode, this.getCustomAttributes)
    }
  },
  async mounted () {
    await this.$store.dispatch('recently-viewed/addItem', this.getCurrentProduct)

    $(document).ready(function(){
      $('.color_button').click(function(){
        console.log('color selected');
        if($(".VueCarousel-slide").hasClass("VueCarousel-slide-active"))
        {
          console.log('class found');
        }
        else {
          console.log('class not found');
        }
        
      });

      $("#story_btn").click(function() {
          $("#story_overlay").fadeIn(300);
          $("#story_container").fadeIn(300);
      });

      $("#close-btn, #story_overlay").click(function() {
          $("#story_overlay").fadeOut(300);
          $("#story_container").fadeOut(300);
      });
      
      $('.tab-navigation button').click(function(){
        $('.tab-navigation button').removeClass('active');
        $(this).addClass('active');
      });

    }); 

  },
  async asyncData ({ store, route, context }) {
    if (context) context.output.cacheTags.add('product')
    const product = await store.dispatch('product/loadProduct', { parentSku: route.params.parentSku, childSku: route && route.params && route.params.childSku ? route.params.childSku : null })
    const loadBreadcrumbsPromise = store.dispatch('product/loadProductBreadcrumbs', { product })
    if (isServer) await loadBreadcrumbsPromise
    catalogHooksExecutors.productPageVisited(product)
  },
  beforeRouteEnter (to, from, next) {
    if (isServer) {
      next()
    } else {
      next((vm) => {
        vm.getQuantity()
      })
    }
  },
  watch: {
    isOnline: {
      handler (isOnline) {
        if (isOnline) {
          this.getQuantity()
        }
      }
    }
  },
  methods: {
    showTab(tabName) {
      // Hide all tabs
      const tabs = document.querySelectorAll('.tab-content');
      tabs.forEach((tab) => {
        tab.style.display = 'none';
      });

      // Show the selected tab
      document.getElementById(tabName).style.display = 'block';
    },
    showDetails (event) {
      this.detailsOpen = true
      event.target.classList.add('hidden')
    },
    notifyOutStock () {
      this.$store.dispatch('notification/spawnNotification', {
        type: 'error',
        message: this.$t(
          'The product is out of stock and cannot be added to the cart!'
        ),
        action1: { label: this.$t('OK') }
      })
    },
    notifyWrongAttributes () {
      this.$store.dispatch('notification/spawnNotification', {
        type: 'warning',
        message: this.$t(
          'No such configuration for the product. Please do choose another combination of attributes.'
        ),
        action1: { label: this.$t('OK') }
      })
    },
    async changeFilter (variant) {
      const selectedConfiguration = Object.assign({ attribute_code: variant.type }, variant)
      await filterChangedProduct(selectedConfiguration, this.$store, this.$router)
      this.getQuantity()
    },
    openSizeGuide () {
      this.$bus.$emit('modal-show', 'modal-sizeguide')
    },
    isOptionAvailable (option) { // check if the option is available
      const currentConfig = Object.assign({}, this.getCurrentProductConfiguration)
      currentConfig[option.type] = option
      return isOptionAvailableAsync(this.$store, { product: this.getCurrentProduct, configuration: currentConfig })
    },
    async getQuantity () {
      if (this.isStockInfoLoading) return // stock info is already loading
      this.isStockInfoLoading = true
      try {
        if (config.products.alwaysSyncPricesClientSide) {
          doPlatformPricesSync([this.getCurrentProduct]);
        }
        const res = await this.$store.dispatch('stock/check', {
          product: this.getCurrentProduct,
          qty: this.getCurrentProduct.qty
        })

        this.manageQuantity = res.isManageStock
        this.maxQuantity = res.isManageStock ? res.qty : null
      } finally {
        this.isStockInfoLoading = false
      }
    },
    handleQuantityError (error) {
      this.quantityError = error
    }
  },
  metaInfo () {
    const storeView = currentStoreView()
    return {
      /* link: [
        { rel: 'amphtml',
          href: this.$router.resolve(localizedRoute({
            name: this.getCurrentProduct.type_id + '-product-amp',
            params: {
              parentSku: this.getCurrentProduct.parentSku ? this.getCurrentProduct.parentSku : this.getCurrentProduct.sku,
              slug: this.getCurrentProduct.slug,
              childSku: this.getCurrentProduct.sku
            }
          }, storeView.storeCode)).href
        }
      ], */
      title: htmlDecode(this.getCurrentProduct.meta_title || this.getCurrentProduct.name),
      meta: this.getCurrentProduct.meta_description ? [{ vmid: 'description', name: 'description', content: htmlDecode(this.getCurrentProduct.meta_description) }] : []
    }
  }
}
</script>

<style lang="scss" scoped>
@import '~theme/css/variables/colors';
@import '~theme/css/helpers/functions/color';
$color-primary: color(primary);
$color-tertiary: color(tertiary);
$color-secondary: color(secondary);
$color-white: color(white);
$bg-secondary: color(secondary, $colors-background);

#story_container {
  display: none;
    position: fixed;
    top: 40%;
    left: 50%;
    -webkit-transform: translate(-50%, -50%);
    -ms-transform: translate(-50%, -50%);
    transform: translate(-50%, -50%);
    background-color: #fff;
    padding: 20px;
    -webkit-box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    border-radius: 8px;
    max-width: 100%;
    max-height: 80%;
    overflow: auto;
    height: 500px;
    width: 800px;
    z-index: 5;

}

#story_overlay {
    display: none;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.5);
}

#close-btn {
  position: absolute;
    top: 10px;
    right: 10px;
    cursor: pointer;
    background: transparent;
    border: none;
    font-weight: 700;
    font-size: 19px;

}
button#story_btn {
    font-size: 14px;
    font-style: normal;
    font-weight: 400;
    line-height: normal;
    background: transparent;
    border: none;
    margin-top: 36px;
    border-bottom: 1px solid;
    padding: 0;
    padding-bottom: 2px;
}
#story_container p {
    font-size: 14px;
    line-height: 21px;
}
.prd_detail_col {
  padding-left: 50px;
}

.product_container {
  max-width:100%;
  width:100%;
  padding-left: 0px;
  padding-right: 0px;
}
.product-top-section {
  padding: 0px;
  margin-top: -4px;
}
.img_slider_col {
  padding-left: 0px;
  padding-right: 0;
}

.product {
  &__add-to-compare {
    display: none;
    @media (min-width: 767px) {
      display: block;
    }
  }
}

.breadcrumbs {
  @media (max-width: 767px) {
    margin: 15px 0;
    padding: 15px 0 0 15px;
  }
}

.error {
  color: red;
  font-weight: bold;
  padding-bottom: 15px;
}
.data {
  @media (max-width: 767px) {
    border-bottom: 1px solid $bg-secondary;
  }
}

.image {
  @media (max-width: 1023px) {
    margin-bottom: 20px;
  }
}

.product-name {
  @media (max-width: 767px) {
    font-size: 36px;
  }
}

.variants-label {
  @media (max-width: 767px) {
    font-size: 14px;
  }
}

.variants-wrapper {
  @media (max-width: 767px) {
    padding-bottom: 30px;
  }

  .sizes {
    @media (max-width: 767px) {
      width: 100%;
    }
  }

  .size-guide {
    height: 40px;
    @media (max-width: 767px) {
      width: 100%;
      margin-left: 0;
    }
  }
}

.product-top-section {
  @media (max-width: 767px) {
    padding: 0;
    background-color: $color-white;
  }
}

.add-to-buttons {
  @media (max-width: 767px) {
    padding-top: 30px;
    margin-bottom: 40px;
  }
}

.details {
  @media (max-width: 767px) {
    padding: 50px 15px 15px;
  }
}

.details-title {
  padding: 0 8px;

  @media (max-width: 767px) {
    font-size: 18px;
    margin: 0;
  }
}

.details-wrapper {
  @media (max-width: 767px) {
    position: relative;
    max-height: 140px;
    overflow: hidden;
    transition: all 0.3s ease;
    font-size: 14px;
  }

  &--open {
    max-height: none;
  }
}

.details-story_overlay {
  @media (max-width: 767px) {
    position: absolute;
    height: 75%;
    bottom: 0;
    left: 0;
    width: 100%;
    margin: 0;
    cursor: pointer;
    background: linear-gradient(rgba($color-white, 0), rgba($color-white, 1));
    &.hidden {
      display: none;
    }
  }
}

.action {
  &:hover {
    color: $color-tertiary;
  }
}

.attributes {
  list-style-type: none;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s;
}

.fade-enter,
.fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}

.product-image {
  /* mix-blend-mode: multiply; */
  width: 460px;
}

.web-share {
  float: right;
  cursor: pointer;
  padding-left: 10px;
}
.product-video {
    width: 100%;
}
.wishlist_cstm {
    float: right;
    color: #969696;
    border-right: 1px solid;
}
.product-name{
    color: #302A2A;
    font-size: 25px;
    font-style: normal;
    font-weight: 400;
    line-height: normal;
    padding-bottom: 15px;
    border-bottom: 1px solid #C1C1C1;
    padding-top: 30px;
}
.cl-secondary {
    color: #828282;
    font-size: 13px;
}
.price-cstm {
  color: #302A2A;
  font-size: 18px;
  font-style: normal;
  font-weight: 400;
  line-height: normal;
}
.short-description {
    color: #302A2A;
    font-size: 15px;
    font-style: normal;
    font-weight: 400;
    line-height: 20px;
    padding-bottom: 40px;
}
.color-bt-border {
  border-bottom: 1px solid #C1C1C1;
  width: 100%;
  padding-bottom: 25px;
}
.bg-cl-secondary{
  background-color: #FFFF;
}
.row.top-xs.m0.pt15.pb40.variants-wrapper{
  display: flex;
    justify-content: space-between;
}
.dv_sticky {
  position: sticky;
  height: fit-content;
  width: 100%;
  top: 20px;
}
/* Tab Styling  */
#productCareTab {
    display: none;
}
#careTab {
    display: none;
}

  .tab-navigation button {
    background-color: #555;
    color: white;
    border: none;
    padding: 10px 20px;
    cursor: pointer;
    transition: background-color 0.3s;
  }

  .tab-navigation button:hover {
    background-color: #777;
  }

  .tab-navigation {
    display: flex;
    background-color: #fff;
    margin-bottom: 20px;
    border-bottom: 1px solid #C1C1C1;
  }

  .tab-navigation button {
    background-color: inherit;
    border: none;
    outline: none;
    cursor: pointer;
    padding: 10px 15px;
    flex: 1;
    transition: background-color 0.3s;
    color: #000;
    text-align: left;
    font-size: 16px;
  }

  .tab-navigation button.active {
    border-bottom: 1px solid #000;
  }

  .tab-navigation button:hover {
    border-bottom: 1px solid #000;
    background-color: transparent;
  }

  .tab-content {
    display: none;
    padding: 40px 20px;
    border: 1px solid #ccc;
  }

  .tab-content.active {
    display: block;
  }

  .details-title {
    color: #333;
    border-bottom:1px solid #ccc;
    padding-bottom: 10px;
    font-weight: 400;
  }

  .details-wrapper {
    margin-top: 20px;
    transition: max-height 0.3s ease-in-out;
    overflow: hidden;
  }

  .details-wrapper--open {
    max-height: 1000px;
  }

  .care_description {
    line-height: 1.5;
  }

  .prd_tab_section {
    margin-top: 50px;
    margin-bottom: 30px;
  }

  .related_prd_div {
      margin-bottom: 50px;
  }

@media only screen and (min-device-width: 320px) and (max-device-width: 767px) {

  .prd_detail_col{
      padding-left: 20px;
      padding-right: 20px;
  }
  .prd_tab_section {
    margin-top: 10px;
    margin-bottom: 0px;
  }
  .related_prd_div .prd_lst_col {
    margin-bottom: 15px;
  }
}


</style>

<style>
  .related_prd_div .product {
    background: #cecece;
  }


@media only screen and (min-device-width: 1200px) and (max-device-width: 1280px) {
  #story_container
  {
    top: 45% !important;
  }
}

@media only screen and (min-device-width: 1281px) and (max-device-width: 1369px) {
  #story_container
  {
    top: 45% !important;
  }
}

@media only screen and (min-device-width: 1370px) and (max-device-width: 1440px) {
  #story_container
  {
    top: 45% !important;
  }
}

@media only screen and (min-device-width: 1441px) and (max-device-width: 1536px) {
  #story_container
  {
    top: 48% !important;
  }
}

@media only screen and (min-device-width: 1537px) and (max-device-width: 1600px) {
  #story_container
  {
    top: 48% !important;
  }
}

@media only screen and (min-device-width: 992px) and (max-device-width: 1199px) {
}


  @media only screen and (min-device-width: 320px) and (max-device-width: 834px) {

    .prd_detail_col{
        padding-left: 20px ;
        padding-right: 20px !important;
    }
    .prd_tab_section {
      margin-top: 10px !important;
      margin-bottom: 0px !important;
    }
    .related_prd_div .prd_lst_col {
      margin-bottom: 15px !important;
    }
    .related_prd_div .product-listing {
        justify-content: unset !important;
    }

    #story_container{
        top: 33% !important;
        height: 400px !important;
        width: 80% !important;
    }

  }



  @media only screen and (min-device-width: 768px) and (max-device-width: 992px) {
      .prd_detail_col {
        padding-left: 30px !important;
      }
  }
</style>
