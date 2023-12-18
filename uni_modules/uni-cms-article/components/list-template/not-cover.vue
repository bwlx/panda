<template>
  <uni-list-item
      :to="'/uni_modules/uni-cms-article/pages/detail/detail?id=' + data._id"
      :key="data._id"
      class="list-item not-cover"
      direction="column"
  >
    <template v-slot:body>
      <view class="main">
        <view>
          <text class="title">{{ data.title }}</text>
        </view>
        <view class="info">
			<view class="author">
				<text>{{ data.user_id[0] ? data.user_id[0].nickname : '' }}</text>
			</view>
			<view class="publish_date">
				<text>{{ publishTime(data.publish_date) }}</text>
			</view>
			<view class="tags">
			  <uni-tag class="tag" type="success" :text="item" v-for="(item, index) in data.tags" :key="index" />
			</view>
		  
		</view>
      </view>
    </template>
  </uni-list-item>
</template>

<script>
import translatePublishTime from "@/uni_modules/uni-cms-article/common/publish-time";

export default {
  name: "not-cover",
  props: {
    data: {
      type: Object,
      default: () => {
        return {}
      }
    }
  },
  methods: {
    // 格式化时间戳
    publishTime(timestamp) {
      return translatePublishTime(timestamp)
    },
  }
}
</script>

<style scoped lang="scss">
@import "./style.scss";
</style>
