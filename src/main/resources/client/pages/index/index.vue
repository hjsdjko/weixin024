<template>
<view class="content">
	<view :style='{"width":"100%","flexWrap":"wrap","background":"#ffffff","display":"flex","height":"100%"}'>
        <z-swiper v-model="swiperList" :options="options2" :style='{"width":"100%","margin":"0 0 20rpx 0","background":"#ffffff","height":"360rpx"}' style="touch-action: none;">
            <z-swiper-item style="touch-action: none;" :style='{"width":"100%","background":"#ffffff","height":"100%"}' v-for="(swiper,index) in swiperList" :key="index" @tap="onSwiperTap(swiper)">
            	<image :style='{"width":"100%","objectFit":"cover","display":"block","height":"100%"}' mode="aspectFill" :src="baseUrl+swiper.img"></image>
            	<view v-if="false" :style='{"width":"100%","padding":"0 8rpx 0 8rpx","lineHeight":"60rpx","fontSize":"28rpx","color":"#333333","background":"#ffffff"}'>{{ swiper.title }}</view>
            </z-swiper-item>
        </z-swiper>

		<view :style='{"padding":"20rpx 0 0 0","alignItems":"center","flex":"1","display":"flex","width":"calc(98% - 120rpx)","position":"relative","justifyContent":"space-between"}'>
			<picker v-if="queryList.length>1" mode="selector" :range="queryList" range-key="queryName" :value="queryIndex" @change="queryChange" style="padding-left: 20upx;" :style='{}'>
				<view>
					<text class="iconfont icon-gengduo2" :style='{}'></text>
				</view>
			</picker>
			<view v-if="queryIndex==0" :style='{"backgroundColor":"#f5f5f5","margin":"0 30rpx 0 30rpx","color":"#333333","alignItems":"center","borderRadius":"0px","flex":"1","display":"flex","lineHeight":"64rpx","fontSize":"24rpx","height":"64rpx"}'>
				<text class="iconfont icon-sousuo1" :style='{"margin":"0 16rpx 0 16rpx"}'></text>
				<input v-model="searchForm.shangpinxinxishangpinmingcheng" type="text" placeholder="商品名称" :style='{"background":"transparent","height":"100%"}'></input>
			</view>
			<button v-if="queryIndex==0" @tap="onPageTap('shangpinxinxi')" :style='{"border":"0px","padding":"0 40rpx 0 40rpx","margin":"0 20rpx 0 0px","borderRadius":"0px","color":"#333","background":"#befaba","fontSize":"28rpx","lineHeight":"64rpx","height":"64rpx"}'>搜索</button>
		</view>

		<!-- menu -->
		<view v-if="true" class="menu" :style='{"padding":"0px 0px 0px 40rpx","margin":"40rpx 0px 20rpx 0px","borderColor":"#eee","borderRadius":"8rpx","flexWrap":"wrap","background":"#ffffff","borderWidth":"0px","display":"flex","width":"100%","borderStyle":"solid","height":"auto"}'>
            <block v-for="(item,ind) in menuList" v-bind:key="item.roleName">
                <block v-if="ind==0" v-bind:key="index" v-for=" (menu,index) in item.frontMenu">
					<view v-if="menu.childs.length" :style='{"width":"calc(25% - 40rpx)","padding":"12rpx 0 12rpx 0","margin":"0px 40rpx 20rpx 0","borderRadius":"16rpx","height":"auto"}' class="menu-list" @tap="menuClick(menu,index)">
						<view class="iconarr" :class="menu.fontClass" :style='{"border":"4rpx solid #d84fa930","padding":"0 0 0 0","margin":"0 auto 12rpx auto","color":"#d84fa9","borderRadius":"400rpx","textAlign":"center","background":"#fff6fb","display":"block","width":"96rpx","lineHeight":"96rpx","fontSize":"60rpx","height":"96rpx"}'></view>
						<view :style='{"padding":"0 0 0 0","margin":"0px auto 0 auto","color":"#333333","textAlign":"center","width":"100%","lineHeight":"1.5","fontSize":"26rpx"}'>{{menu.menu}}</view>
					</view>
                </block>
            </block>
		</view>
		<!-- menu -->
		
		

		<!-- 商品推荐 -->
		<view class="listBox recommend" :style='{"width":"100%","margin":"40rpx 0 40rpx 0","background":"#ffffff","order":"2"}'>
			<view v-if="false && 3 == 1" class="idea recommendIdea" :style='{"padding":"40rpx","flexWrap":"wrap","background":"url(http://codegen.caihongy.cn/20230815/1b3e2caf374142fcb4d5bdb9448d4e01.png) no-repeat center bottom / cover","display":"block","width":"100%","justifyContent":"space-between","height":"360rpx"}'>
				<view :style='{"width":"100%","margin":"100rpx 0 0 0","textAlign":"center","background":"none","display":"block","height":"auto"}' class="box box1">学会选择，学会放弃；</view>
				<view :style='{"width":"100%","textAlign":"center","background":"none","display":"block","height":"auto"}' class="box box2">耐得住寂寞，经得起诱惑。</view>
				<view :style='{"width":"20%","background":"#ffffff","display":"none","height":"160rpx"}' class="box box3"></view>
				<view :style='{"width":"20%","background":"#ffffff","display":"none","height":"160rpx"}' class="box box4"></view>
			</view>
			
			<view class="title" :style='{"width":"calc(100% - 48rpx)","padding":"20rpx 80rpx 20rpx 80rpx","margin":"0 24rpx 24rpx 24rpx","textAlign":"center","background":"url(http://clfile.zggen.cn/20231201/929f7c0aed824bb3959e8ba0641392c8.gif) no-repeat center center / 100%","height":"auto"}'>
				<view :style='{"padding":"0","color":"#d84fa9","borderRadius":"0px","textAlign":"center","background":"none","display":"inline-block","width":"auto","fontSize":"36rpx","lineHeight":"40rpx","minWidth":"300rpx","fontWeight":"500"}'>商品信息推荐</view>
			</view>
			
			<view v-if="false && 3 == 2" class="idea recommendIdea" :style='{"padding":"40rpx","flexWrap":"wrap","background":"url(http://codegen.caihongy.cn/20230815/1b3e2caf374142fcb4d5bdb9448d4e01.png) no-repeat center bottom / cover","display":"block","width":"100%","justifyContent":"space-between","height":"360rpx"}'>
				<view :style='{"width":"100%","margin":"100rpx 0 0 0","textAlign":"center","background":"none","display":"block","height":"auto"}' class="box box1">学会选择，学会放弃；</view>
				<view :style='{"width":"100%","textAlign":"center","background":"none","display":"block","height":"auto"}' class="box box2">耐得住寂寞，经得起诱惑。</view>
				<view :style='{"width":"20%","background":"#ffffff","display":"none","height":"160rpx"}' class="box box3"></view>
				<view :style='{"width":"20%","background":"#ffffff","display":"none","height":"160rpx"}' class="box box4"></view>
			</view>
			
			
			
			
			  
			
			<!-- 样式6 -->
			<view class="list-box style6" :style='{"width":"100%","padding":"24rpx 24rpx 24rpx 24rpx","margin":"0 0 0 0","height":"auto"}'>
				<view v-if="shangpinxinxilist.length > 0" @tap="onDetailTap('shangpinxinxi',shangpinxinxilist[0].id)" class="box box1" :style='{"width":"100%","padding":"0 0 0 0","margin":"0 0 20rpx 0","position":"relative","height":"auto"}'>
					<view v-if="true" :style='{"padding":"0 20rpx 0 20rpx","margin":"0 0 0 0","overflow":"hidden","whiteSpace":"nowrap","color":"#333","textAlign":"center","width":"100%","lineHeight":"64rpx","fontSize":"28rpx","textOverflow":"ellipsis"}' class="title ">{{shangpinxinxilist[0].shangpinmingcheng}}</view>
					<view v-if="true" :style='{"padding":"0 20rpx 0 20rpx","margin":"0 0 0 0","overflow":"hidden","whiteSpace":"nowrap","color":"#333","textAlign":"center","width":"100%","lineHeight":"64rpx","fontSize":"28rpx","textOverflow":"ellipsis"}' class="title ">{{shangpinxinxilist[0].shangpinfenlei}}</view>
					<image :style='{"width":"100%","objectFit":"cover","display":"block","height":"328rpx"}' class="list-item-image" mode="aspectFill" v-if="shangpinxinxilist[0].shangpintupian.substring(0,4)=='http'" :src="shangpinxinxilist[0].shangpintupian"></image>
					<image :style='{"width":"100%","objectFit":"cover","display":"block","height":"328rpx"}' class="list-item-image" mode="aspectFill" v-else :src="shangpinxinxilist[0].shangpintupian?baseUrl+shangpinxinxilist[0].shangpintupian.split(',')[0]:''"></image>
				</view>
				<view class="list-item" :style='{"width":"100%","margin":"0 0 20rpx 0","justifyContent":"space-between","display":"flex","height":"auto"}'>
					<view class="list-item-body" :style='{"width":"48%","padding":"0 0 0 0","margin":"0 0 0 0","height":"auto"}'>
						<view v-if="shangpinxinxilist.length > 1" @tap="onDetailTap('shangpinxinxi',shangpinxinxilist[1].id)" class="box box2" :style='{"width":"100%","padding":"0 0 0 0","margin":"0 0 20rpx 0","position":"relative","height":"auto"}'>
							<view v-if="true" :style='{"padding":"0 20rpx 0 20rpx","margin":"0 0 0 0","overflow":"hidden","whiteSpace":"nowrap","color":"#333","textAlign":"center","width":"100%","lineHeight":"64rpx","fontSize":"28rpx","textOverflow":"ellipsis"}' class="title ">{{shangpinxinxilist[1].shangpinmingcheng}}</view>
							<view v-if="true" :style='{"padding":"0 20rpx 0 20rpx","margin":"0 0 0 0","overflow":"hidden","whiteSpace":"nowrap","color":"#333","textAlign":"center","width":"100%","lineHeight":"64rpx","fontSize":"28rpx","textOverflow":"ellipsis"}' class="title ">{{shangpinxinxilist[1].shangpinfenlei}}</view>
							<image :style='{"width":"100%","objectFit":"cover","display":"block","height":"328rpx"}' class="list-item-image" mode="aspectFill" v-if="shangpinxinxilist[1].shangpintupian.substring(0,4)=='http'" :src="shangpinxinxilist[1].shangpintupian"></image>
							<image :style='{"width":"100%","objectFit":"cover","display":"block","height":"328rpx"}' class="list-item-image" mode="aspectFill" v-else :src="shangpinxinxilist[1].shangpintupian?baseUrl+shangpinxinxilist[1].shangpintupian.split(',')[0]:''"></image>
						</view>
						<view v-if="shangpinxinxilist.length > 2" @tap="onDetailTap('shangpinxinxi',shangpinxinxilist[2].id)" class="box box3" :style='{"width":"100%","padding":"0 0 0 0","margin":"0 0 0 0","position":"relative","height":"auto"}'>
							<view v-if="true" :style='{"padding":"0 20rpx 0 20rpx","margin":"0 0 0 0","overflow":"hidden","whiteSpace":"nowrap","color":"#333","textAlign":"center","width":"100%","lineHeight":"64rpx","fontSize":"28rpx","textOverflow":"ellipsis"}' class="title ">{{shangpinxinxilist[2].shangpinmingcheng}}</view>
							<view v-if="true" :style='{"padding":"0 20rpx 0 20rpx","margin":"0 0 0 0","overflow":"hidden","whiteSpace":"nowrap","color":"#333","textAlign":"center","width":"100%","lineHeight":"64rpx","fontSize":"28rpx","textOverflow":"ellipsis"}' class="title ">{{shangpinxinxilist[2].shangpinfenlei}}</view>
							<image :style='{"width":"100%","objectFit":"cover","display":"block","height":"240rpx"}' class="list-item-image" mode="aspectFill" v-if="shangpinxinxilist[2].shangpintupian.substring(0,4)=='http'" :src="shangpinxinxilist[2].shangpintupian"></image>
							<image :style='{"width":"100%","objectFit":"cover","display":"block","height":"240rpx"}' class="list-item-image" mode="aspectFill" v-else :src="shangpinxinxilist[2].shangpintupian?baseUrl+shangpinxinxilist[2].shangpintupian.split(',')[0]:''"></image>
						</view>
					</view>
					<view class="list-item-body" :style='{"width":"48%","padding":"0 0 0 0","margin":"0 0 0 0","height":"auto"}'>
						<view v-if="shangpinxinxilist.length > 3" @tap="onDetailTap('shangpinxinxi',shangpinxinxilist[3].id)" class="box box4" :style='{"width":"100%","padding":"0 0 0 0","margin":"0 0 20rpx 0","position":"relative","height":"auto"}'>
							<view v-if="true" :style='{"padding":"0 20rpx 0 20rpx","margin":"0 0 0 0","overflow":"hidden","whiteSpace":"nowrap","color":"#333","textAlign":"center","width":"100%","lineHeight":"64rpx","fontSize":"28rpx","textOverflow":"ellipsis"}' class="title ">{{shangpinxinxilist[3].shangpinmingcheng}}</view>
							<view v-if="true" :style='{"padding":"0 20rpx 0 20rpx","margin":"0 0 0 0","overflow":"hidden","whiteSpace":"nowrap","color":"#333","textAlign":"center","width":"100%","lineHeight":"64rpx","fontSize":"28rpx","textOverflow":"ellipsis"}' class="title ">{{shangpinxinxilist[3].shangpinfenlei}}</view>
							<image :style='{"width":"100%","objectFit":"cover","display":"block","height":"240rpx"}' class="list-item-image" mode="aspectFill" v-if="shangpinxinxilist[3].shangpintupian.substring(0,4)=='http'" :src="shangpinxinxilist[3].shangpintupian"></image>
							<image :style='{"width":"100%","objectFit":"cover","display":"block","height":"240rpx"}' class="list-item-image" mode="aspectFill" v-else :src="shangpinxinxilist[3].shangpintupian?baseUrl+shangpinxinxilist[3].shangpintupian.split(',')[0]:''"></image>
						</view>
						<view v-if="shangpinxinxilist.length > 4" @tap="onDetailTap('shangpinxinxi',shangpinxinxilist[4].id)" class="box box5" :style='{"width":"100%","padding":"0 0 0 0","margin":"0 0 0 0","position":"relative","height":"auto"}'>
							<view v-if="true" :style='{"padding":"0 20rpx 0 20rpx","margin":"0 0 0 0","overflow":"hidden","whiteSpace":"nowrap","color":"#333","textAlign":"center","width":"100%","lineHeight":"64rpx","fontSize":"28rpx","textOverflow":"ellipsis"}' class="title ">{{shangpinxinxilist[4].shangpinmingcheng}}</view>
							<view v-if="true" :style='{"padding":"0 20rpx 0 20rpx","margin":"0 0 0 0","overflow":"hidden","whiteSpace":"nowrap","color":"#333","textAlign":"center","width":"100%","lineHeight":"64rpx","fontSize":"28rpx","textOverflow":"ellipsis"}' class="title ">{{shangpinxinxilist[4].shangpinfenlei}}</view>
							<image :style='{"width":"100%","objectFit":"cover","display":"block","height":"328rpx"}' class="list-item-image" mode="aspectFill" v-if="shangpinxinxilist[4].shangpintupian.substring(0,4)=='http'" :src="shangpinxinxilist[4].shangpintupian"></image>
							<image :style='{"width":"100%","objectFit":"cover","display":"block","height":"328rpx"}' class="list-item-image" mode="aspectFill" v-else :src="shangpinxinxilist[4].shangpintupian?baseUrl+shangpinxinxilist[4].shangpintupian.split(',')[0]:''"></image>
						</view>
					</view>
				</view>
				<view v-if="shangpinxinxilist.length > 5" @tap="onDetailTap('shangpinxinxi',shangpinxinxilist[5].id)" class="box box6" :style='{"width":"100%","padding":"0 0 0 0","margin":"0 0 0 0","position":"relative","display":"none","height":"auto"}'>
					<view v-if="true" :style='{"padding":"0 20rpx 0 20rpx","margin":"0 0 0 0","color":"#333","textAlign":"center","width":"100%","lineHeight":"64rpx","fontSize":"28rpx"}' class="title ">{{shangpinxinxilist[5].shangpinmingcheng}}</view>
					<view v-if="true" :style='{"padding":"0 20rpx 0 20rpx","margin":"0 0 0 0","color":"#333","textAlign":"center","width":"100%","lineHeight":"64rpx","fontSize":"28rpx"}' class="title ">{{shangpinxinxilist[5].shangpinfenlei}}</view>
					<image :style='{"width":"100%","objectFit":"cover","display":"block","height":"328rpx"}' class="list-item-image" mode="aspectFill" v-if="shangpinxinxilist[5].shangpintupian.substring(0,4)=='http'" :src="shangpinxinxilist[5].shangpintupian"></image>
					<image :style='{"width":"100%","objectFit":"cover","display":"block","height":"328rpx"}' class="list-item-image" mode="aspectFill" v-else :src="shangpinxinxilist[5].shangpintupian?baseUrl+shangpinxinxilist[5].shangpintupian.split(',')[0]:''"></image>
				</view>
			</view>
			
			  
			
			  
			<view v-if="false && 3 == 3" class="idea recommendIdea" :style='{"padding":"40rpx","flexWrap":"wrap","background":"url(http://codegen.caihongy.cn/20230815/1b3e2caf374142fcb4d5bdb9448d4e01.png) no-repeat center bottom / cover","display":"block","width":"100%","justifyContent":"space-between","height":"360rpx"}'>
				<view :style='{"width":"100%","margin":"100rpx 0 0 0","textAlign":"center","background":"none","display":"block","height":"auto"}' class="box box1">学会选择，学会放弃；</view>
				<view :style='{"width":"100%","textAlign":"center","background":"none","display":"block","height":"auto"}' class="box box2">耐得住寂寞，经得起诱惑。</view>
				<view :style='{"width":"20%","background":"#ffffff","display":"none","height":"160rpx"}' class="box box3"></view>
				<view :style='{"width":"20%","background":"#ffffff","display":"none","height":"160rpx"}' class="box box4"></view>
			</view>
		</view>
		<!-- 商品推荐 -->
		
		

		<!-- 商品列表 -->
																																																<!-- 商品列表 -->
		
		
		<!-- 新闻资讯 -->
														<view class="listBox news" :style='{"width":"100%","margin":"40rpx 0 40rpx 0","background":"#ffffff","order":"8"}'>
			<view v-if="false && 3 == 1" class="idea newsIdea" :style='{"width":"100%","padding":"40rpx","flexWrap":"wrap","background":"url(http://codegen.caihongy.cn/20230815/1b3e2caf374142fcb4d5bdb9448d4e01.png) no-repeat center bottom / 100% 100%","display":"block","height":"360rpx"}'>
				<view :style='{"width":"100%","margin":"100rpx 0 0 0","textAlign":"center","background":"none","display":"block","height":"auto"}' class="box box1">走的够远，才懂得前方依旧长路漫漫</view>
				<view :style='{"width":"20%","background":"#ffffff","display":"none","height":"160rpx"}' class="box box2"></view>
				<view :style='{"width":"20%","background":"#ffffff","display":"none","height":"160rpx"}' class="box box3"></view>
				<view :style='{"width":"20%","background":"#ffffff","display":"none","height":"160rpx"}' class="box box4"></view>
			</view>
			
			<view class="title" :style='{"width":"calc(100% - 48rpx)","padding":"20rpx 80rpx ","margin":"0 24rpx 24rpx 24rpx","textAlign":"center","background":"url(http://clfile.zggen.cn/20231201/929f7c0aed824bb3959e8ba0641392c8.gif) no-repeat center center / 100%","height":"auto"}'>
				<view :style='{"padding":"0","color":"#d84fa9","borderRadius":"0px","background":"none","display":"inline-block","fontSize":"36rpx","lineHeight":"40rpx","minWidth":"300rpx","fontWeight":"500"}'>知识普及</view>
				<text :style='{"margin":"0px 0 0 0","color":"#999","display":"inline-block","width":"auto","fontSize":"28rpx","lineHeight":"40rpx","float":"right"}' @tap="onPageTap('news')">查看更多</text>
			</view>
			
			<view v-if="false && 3 == 2" class="idea newsIdea" :style='{"width":"100%","padding":"40rpx","flexWrap":"wrap","background":"url(http://codegen.caihongy.cn/20230815/1b3e2caf374142fcb4d5bdb9448d4e01.png) no-repeat center bottom / 100% 100%","display":"block","height":"360rpx"}'>
				<view :style='{"width":"100%","margin":"100rpx 0 0 0","textAlign":"center","background":"none","display":"block","height":"auto"}' class="box box1">走的够远，才懂得前方依旧长路漫漫</view>
				<view :style='{"width":"20%","background":"#ffffff","display":"none","height":"160rpx"}' class="box box2"></view>
				<view :style='{"width":"20%","background":"#ffffff","display":"none","height":"160rpx"}' class="box box3"></view>
				<view :style='{"width":"20%","background":"#ffffff","display":"none","height":"160rpx"}' class="box box4"></view>
			</view>
			
					  
						
						
		  <!-- 样式4 -->
		  		  <view class="news-box1" :style='{"width":"100%","padding":"24rpx 24rpx 24rpx 24rpx","margin":"40rpx 0 0 0","height":"auto"}'>
			<view @tap="onNewsDetailTap(item.id)" v-for="(item,index) in news" :key="index" class="list-item" :style='{"padding":"0 0 24rpx 0","margin":"0 0 24rpx 0","borderColor":"#f0b8dd","flexWrap":"wrap","borderWidth":"0 0 2rpx 0","display":"flex","width":"100%","borderStyle":"dotted","height":"auto"}'>
			  <view class="list-item-body" :style='{"width":"calc(100% - 260rpx)","padding":"0 0 0 0","margin":"0 0 0 0","order":"2","height":"200rpx"}'>
				<view :style='{"padding":"0 20rpx 0 20rpx","margin":"0 0 0 0","overflow":"hidden","whiteSpace":"nowrap","color":"#333","width":"100%","lineHeight":"60rpx","fontSize":"28rpx","textOverflow":"ellipsis","height":"60rpx"}' class="title ">{{item.title}}</view>
				<view :style='{"padding":"0 20rpx 0 20rpx","margin":"0 0 0 0","overflow":"hidden","color":"#999","textAlign":"left","width":"100%","lineHeight":"48rpx","fontSize":"28rpx","height":"96rpx"}' class="desc ">{{item.introduction}}</view>
				<view :style='{"padding":"0 20rpx 0 20rpx","margin":"0 0 0 0","color":"#999","textAlign":"right","width":"100%","lineHeight":"48rpx","fontSize":"26rpx"}' class="time">{{item.addtime.split(" ")[0]}}</view>
			  </view>
			  <image :style='{"width":"240rpx","objectFit":"cover","borderRadius":"0px","display":"block","height":"200rpx","order":"1"}' mode="aspectFill" class="listmpic" :src="baseUrl+item.picture"></image>
			</view>
		  </view>
		  		  
		  <!-- 样式5 -->
		  		  
		  <!-- 样式6 -->
		  		  
		  <!-- 样式7 -->
		  		  
		  <!-- 样式8 -->
		  		  
		  <!-- 样式9 -->
		  			
			<view v-if="false && 3 == 3" class="idea newsIdea" :style='{"width":"100%","padding":"40rpx","flexWrap":"wrap","background":"url(http://codegen.caihongy.cn/20230815/1b3e2caf374142fcb4d5bdb9448d4e01.png) no-repeat center bottom / 100% 100%","display":"block","height":"360rpx"}'>
				<view :style='{"width":"100%","margin":"100rpx 0 0 0","textAlign":"center","background":"none","display":"block","height":"auto"}' class="box box1">走的够远，才懂得前方依旧长路漫漫</view>
				<view :style='{"width":"20%","background":"#ffffff","display":"none","height":"160rpx"}' class="box box2"></view>
				<view :style='{"width":"20%","background":"#ffffff","display":"none","height":"160rpx"}' class="box box3"></view>
				<view :style='{"width":"20%","background":"#ffffff","display":"none","height":"160rpx"}' class="box box4"></view>
			</view>
		</view>
																																						<!-- 新闻资讯 -->
				

	</view>
</view>
</template>

<script>
    import menu from '@/utils/menu'
	import '@/assets/css/global-restaurant.css'
	import uniIcons from "@/components/uni-ui/lib/uni-icons/uni-icons.vue"
	export default {
		components: {
			uniIcons
		},
		data() {
			return {
				options2: {
					effect: 'flip',
					loop : true
				},
				options3: {
					effect: 'cube',
					loop : true,
					cubeEffect: {
						shadow: true,
						slideShadows: true,
						shadowOffset: 20,
						shadowScale: 0.94,
					}
				},
				rows: 2,
				column: 4,
                role : '',
                menuList: [],
                swiperMenuList:[],
                user: {},
                tableName:'',
				btnColor: ['#409eff','#67c23a','#909399','#e6a23c','#f56c6c','#356c6c','#351c6c','#f093a9','#a7c23a','#104eff','#10441f','#a21233','#503319'],
				queryList:[
					{
						queryName:"商品名称",
					},
				],
				queryIndex: 0,
				searchForm:{
					shangpinxinxishangpinmingcheng:'',
				},
				CustomBar: '0',

				//轮播
				swiperList: [],
				shangpinxinxilist: [],
				news: [],
			}
		},
		computed: {
			baseUrl() {
				return this.$base.url;
			}
		},
        async onLoad(){
            
        },
		async onShow() {
			this.swiperMenuList = []
			let table = uni.getStorageSync("nowTable");
			let res = await this.$api.session(table);
			this.user = res.data;
			this.tableName = table;
			let menus = menu.list();
			this.menuList = menus;
			let role = '管理员'
			this.menuList.forEach((item,key) => {
			    if(role==item.roleName) {
			        item.frontMenu.forEach((item2,key2) => {
						if(item2.child.length) {
							item2.childs = []
						    item2.child.forEach((item3,key3)=>{
								if(item3.buttons.indexOf("查看")>-1){
									item2.childs.push(item3)
									this.swiperMenuList.push(item3);
								}
							})
						}
			            
			        })
			    }
			})
            this.btnColor = this.btnColor.sort(()=> {
                    return (0.5-Math.random());
            });
            // let res;
			// 轮播图
			let swiperList = []
			res = await this.$api.list('config', {
				page: 1,
				limit: 5
			});
			for (let item of res.data.list) {
				if (item.value && item.value!="" && item.value!=null ) {
					swiperList.push({
						img: item.value,
                        title: item.name
					});
				}
			}
			if (swiperList) {
				this.swiperList = swiperList;
			}
			// 知识普及
			res = await this.$api.list('news', {
				page: 1,
				limit: 6
			});
			this.news = res.data.list

			// 推荐信息
			if(uni.getStorageSync("userid")) {
				res = await this.$api.recommend2('shangpinxinxi', {                                              
                    page: 1,
                    limit: 6
                });
			} else {
				res = await this.$api.recommend('shangpinxinxi', {                                              
                    page: 1,
                    limit:6 
                });
			}
			this.shangpinxinxilist = res.data.list

		},

		methods: {

			//查询条件切换
			queryChange(e) {
				this.queryIndex=e.detail.value;
				this.searchForm.shangpinxinxishangpinmingcheng="";
			},
			//轮播图跳转
			onSwiperTap(e) {

			},
			// 新闻详情
			onNewsDetailTap(id) {
				this.$utils.jump(`../news-detail/news-detail?id=${id}`)
			},
			// 推荐列表点击详情
			onDetailTap(tableName, id) {
				this.$utils.jump(`../${tableName}/detail?id=${id}`)
			},
			onPageTap(tableName){
				if(tableName=='news'){
					uni.navigateTo({
						url: `../news-list/news-list`,
						fail: function(){
							uni.switchTab({
								url: `../news-list/news-list`
							});
						}
					});
					return false
				}
				if(this.queryIndex==0) {
					uni.setStorageSync('indexQueryCondition',this.searchForm.shangpinxinxishangpinmingcheng);
					this.searchForm.shangpinxinxishangpinmingcheng = '';
				}

				uni.navigateTo({
					url: `../${tableName}/list`,
					fail: function(){
						uni.switchTab({
							url: `../${tableName}/list`
						});
					}
				});
				// this.$utils.jump(`../${tableName}/list`)
			},
			menuClick(menu, index) {
				if (menu.childs.length > 0 && menu.childs.length == 1) {
					uni.navigateTo({
						url: `../${menu.childs[0].tableName}/list`,
						fail: function() {
							uni.switchTab({
								url: `../${menu.childs[0].tableName}/list`
							});
						}
					});
				} else if (menu.childs.length > 1) {
					let arr = []
					for(let x in menu.childs){
						arr.push(menu.childs[x].menu.length>6?menu.childs[x].menu.substring(0,6):menu.childs[x].menu)
					}
					uni.showActionSheet({
						itemList: arr,
						success: function (res) {
							uni.navigateTo({
								url: `../${menu.childs[res.tapIndex].tableName}/list`,
								fail: function() {
									uni.switchTab({
										url: `../${menu.childs[res.tapIndex].tableName}/list`
									});
								}
							});
						}
					});
				}
			},
		}
	}
</script>

<style lang="scss" scoped>
	.content {
		min-height: calc(100vh - 44px);
		box-sizing: border-box;
	}
</style>
