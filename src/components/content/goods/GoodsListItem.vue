<template>
  <div class="goods" @click="toDetail">
<!--    图片懒加载插件v-lazy-->
    <img v-lazy="showImage" alt="" @load="imgLoad" >
    <div class="goods-info">
      <p>{{goodsItem.title}}</p>
      <span class="price">{{goodsItem.price}}</span>
      <span class="collect">{{goodsItem.cfav}}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "GoodsListItem",
  props: {
    goodsItem: {
      type: Object,
      default() {
        return {}
      }
    },
  },
  computed: {
    showImage() {
      return this.goodsItem.image || this.goodsItem.show.img
    }
  },
  methods: {
    imgLoad() {
      this.$bus.$emit('itemImgLoad')
    },
    toDetail() {
      // console.log("跳转到详情页");
      this.$router.push('/detail/' + this.goodsItem.iid)
    }
  }
}
</script>

<style scoped>
.goods {
  width: 48%;
  padding-bottom: 40px;
  position: relative;
}
.goods img {
  width: 100%;
  border-radius: 5px;
}

.goods-info {
  font-size: 12px;
  position: absolute;
  bottom: 5px;
  left: 0;
  right: 0;
  overflow: hidden;
  text-align: center;
}

.goods-info p {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
  margin-bottom: 3px;
}

.goods-info .price {
  color: var(--color-high-text);
  margin-right: 20px;
}

.goods-info .collect {
  position: relative;
}

.goods-info .collect::before {
  content: '';
  position: absolute;
  left: -15px;
  top: 0;
  width: 14px;
  height: 14px;
  background: url("~assets/img/common/collect.svg") 0 0/14px 14px;
}
</style>