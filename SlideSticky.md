## 滑动置顶解决方案

> 使用Android Design Support Library中的 CoordinatorLayout可以完美实现这个功能，云阅已经实现这个效果，具体见页面：[CategoryDetailActivity](https://github.com/youlookwhat/CloudReader/blob/master/app/src/main/java/com/example/jingbin/cloudreader/ui/wan/child/CategoryDetailActivity.java)

| 项目 |介绍与问题|预览|
| -------- |:--:|:--:|
| [Android-StickyNavLayout][1] | An android library for navigator that stick on the top【问题：往上或下惯性滑动时，会卡在悬浮栏那里】 | ![][101]|
| [NetEaseProfileDemo][2] | 仿照网易云音乐歌手资料页面滑动效果实现的Demo | ![][102]|
| [StickyHeaderListView][10] | 打造炫酷列表之 StickyHeaderListView：标题渐变、吸附悬浮、筛选分类、动态头部等 | ![][110]|
| [stickyViewpager][4] | [deprecated] sticky view in viewpager which includes scrollview and listview - viewpager with headers | ![][104]|
| [Stickheaderlayout][11] | 滑动置顶，可拓展性强，唯一的缺点是不可一次推上去 | ![][111]|
| [StickViewLayout][12] | 仿原京东商品详情页，上拉Tab置顶，可查看图文详情，参数详情，商品评论。【问题：1.每次切换都会回到最顶端，2.当其中一个view的内容没有占满全屏，悬浮栏会下移】 | ![][112]|
| [StickyHeaderViewPager][13] | An Android library supports sticking the navigator on the top when ItemView scrolls in Viewpager. | ![][113]|
| [ScrollableLayout][14] | Add a headview for any view and supports sticking the navigator on the top when ItemView scrolls. | ![][114]|
| [TouchEventBus][15] | 一种处理嵌套和非嵌套滑动冲突的解决方案 | ![][115]|
| [ParallaxHeaderViewPager][6] | Scrollable fragments within a viewpager that allows for parallax image and sticky bar effects | ![][106]|
| [appbarlayout-spring-behavior][7] | One Behavior help AppBarLayout to scroll spring and with fling fix app bar | ![][107]|
| [StickScrollView][9] | 仿饿了么滑动置顶双列表联动 | ![][109]|
| [GoodsInfoPage][3] | 仿京东、天猫app的商品详情页的布局架构, 以及功能实现 | ![][103]|
| [DoubleScrollVIew][8] | android仿京东、淘宝商品详情页上拉查看详情 | ![][108]|
| [VerticalSlideFragment][5] | vertical slide to switch to the next fragment page, looks like vertical viewpager | ![][105]|
| [CoordinatorTabLayout][16] | Combination of TabLayout and CoordinatorLayout./TabLayout和CoordinatorLayout相结合的折叠控件 | ![][116]|
| [behavior-learn(Kotlin)][17] | CoordinatorLayout 自定义Behavior 高仿美团商家详情界面 实现页面内容复杂联动效果 | ![][117]|
| [MultiScrollDemo][18] | 使用NestedScrollView+ViewPager+RecyclerView+SmartRefreshLayout打造酷炫下拉视差效果并解决各种滑动冲突 | ![][118]|
| [StickLayout][19] | 使用嵌套实现ViewPager和header的联动效果 | ![][119]|
| [MDStudy][20] | 仿拉勾首页交互效果 | ![][120]|
| [ELeMaList][21] | 仿饿了么商品列表页面（用Kotlin实现） | ![][121]|
| [StikkyHeader][22] | This is a very simple library for Android that allows you to stick an header to a scrollable view and easily apply animation to it | ![][122]|
| [DragTopLayout][23] | Sometimes we need to show a top view above a ViewPager or ListView. DragTopLayout is a ViewGroup that contains a content view and a top menu view. You can show the top menu view just drag down the content view at the right time, or drag it up to fold. | ![][123]|
| [ViewPagerHeaderScrollDemo][24] | 简单来说想在 ViewPager 上方加一个 Header，当 ViewPager 内部滚动时，同时或者优先滚动顶部的 Header | ![][124]|
| [HeaderLayout][25] | 头部联动控件，适用于详情页，只需在XML中配置即可实现网易云歌手详情界面的滑动效果 | ![][125]|

<!--项目链接-->
[1]:https://github.com/sangmingming/Android-StickyNavLayout
[2]:https://blog.csdn.net/u011734444/article/details/51471182
[3]:https://github.com/hexianqiao3755/GoodsInfoPage
[4]:https://github.com/xmuSistone/stickyViewpager
[5]:https://github.com/xmuSistone/VerticalSlideFragment
[6]:https://github.com/boxme/ParallaxHeaderViewPager
[7]:https://github.com/ToDou/appbarlayout-spring-behavior
[8]:https://github.com/ysnows/DoubleScrollVIew
[9]:https://github.com/WelliJohn/StickScrollView
[10]:https://github.com/sfsheng0322/StickyHeaderListView
[11]:https://github.com/yang747046912/Stickheaderlayout
[12]:https://github.com/youlookwhat/StickViewLayout
[13]:https://github.com/w446108264/StickyHeaderViewPager
[14]:https://github.com/w446108264/ScrollableLayout
[15]:https://github.com/YvesCheung/TouchEventBus/blob/master/README_NESTEDSCROLL.md
[16]:https://github.com/hugeterry/CoordinatorTabLayout
[17]:https://github.com/iielse/behavior-learn
[18]:https://github.com/SiberiaDante/MultiScrollDemo
[19]:https://juejin.im/entry/5b1f2bb7f265da6e02460812
[20]:https://github.com/Goach/MDStudy
[21]:https://github.com/leiyun1993/ELeMaList
[22]:https://github.com/carlonzo/StikkyHeader
[23]:https://github.com/chenupt/DragTopLayout
[24]:https://github.com/ongakuer/ViewPagerHeaderScrollDemo
[25]:https://github.com/imurluck/HeaderLayout

<!--图片链接 依次对应-->
[101]:https://github.com/sangmingming/Android-StickyNavLayout/blob/master/sc.gif?raw=true
[102]:https://img-blog.csdn.net/20160523110212030?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast
[103]:https://github.com/hexianqiao3755/GoodsInfoPage/raw/master/art/demo.gif
[104]:https://github.com/xmuSistone/stickyViewpager/blob/master/gif01.gif?raw=true
[105]:https://github.com/xmuSistone/VerticalSlideFragment/blob/master/capture.gif?raw=true
[106]:https://upload-images.jianshu.io/upload_images/1354448-77ba8fe85699b899.gif?imageMogr2/auto-orient/strip
[107]:https://github.com/ToDou/appbarlayout-spring-behavior/blob/master/screenshot/appbar_spring_blur_tab.gif?raw=true
[108]:https://github.com/ysnows/DoubleScrollVIew/blob/master/a.gif?raw=true
[109]:https://github.com/WelliJohn/StickScrollView/raw/master/imgs/%E4%BB%BF%E9%A5%BF%E4%BA%86%E4%B9%88%E5%88%97%E8%A1%A8%E9%A1%B5.gif?raw=true
[110]:https://github.com/sfsheng0322/StickyHeaderListView/raw/master/resources/stickyheader.gif
[111]:https://raw.githubusercontent.com/yang747046912/Stickheaderlayout/master/image/pp.gif
[112]:https://github.com/youlookwhat/StickViewLayout/raw/master/sample.gif?raw=true
[113]:https://github.com/w446108264/StickyHeaderViewPager/raw/master/output/big.gif
[114]:https://github.com/w446108264/ScrollableLayout/raw/master/output/show.gif
[115]:https://raw.githubusercontent.com/YvesCheung/TouchEventBus/master/img/nestedScrollPreview.gif
[116]:https://github.com/hugeterry/CoordinatorTabLayout/raw/master/showUI/show1.gif
[117]:https://github.com/iielse/behavior-learn/raw/master/preview2.gif
[118]:https://github.com/SiberiaDante/MultiScrollDemo/raw/master/assets/GIF.gif
[119]:https://user-gold-cdn.xitu.io/2018/6/12/163f1c3ca4c4f60b?imageslim
[120]:https://camo.githubusercontent.com/674e4b9f11386b3214d68266cf539a29385978de/68747470733a2f2f75706c6f61642d696d616765732e6a69616e7368752e696f2f75706c6f61645f696d616765732f323134383231372d623734336530353539616431353934632e6769663f696d6167654d6f6772322f6175746f2d6f7269656e742f7374726970
[121]:https://github.com/leiyun1993/ELeMaList/raw/master/screenshot/3.gif
[122]:https://raw.githubusercontent.com/carlonzo/StikkyHeader/develop/readme/example1.gif
[123]:https://raw.githubusercontent.com/chenupt/DragTopLayout/master/imgs/dragtop_1.1.0.gif
[124]:https://raw.githubusercontent.com/ongakuer/ViewPagerHeaderScrollDemo/master/screenshot.gif
[125]:https://github.com/imurluck/HeaderLayout/raw/master/screenshots/HeaderLayout.gif
