![fragrans_icon](https://github.com/chadhea/Fragrans_image/blob/master/fragrans_icon.png)
类属性与方法扩展

Installation with CocoaPods  
Podfile  
To integrate Fragrans into your Xcode project using CocoaPods, specify it in your Podfile:  
```
source 'https://github.com/CocoaPods/Specs.git'
platform :ios, '8.0'

target 'TargetName' do
pod 'Fragrans', '~> 0.0.3'
end
```  
部分代码示例  
=

NSURLRequest+Fragrans  
```
//get
[NSURLRequest get_requestWithURL:@"" params:nil   completionHandler:^(NSDictionary * _Nonnull response, NSError * _Nonnull error) {
     //数据解析
}];
//post
[NSURLRequest post_requestWithURL:@"xxx" params:@{}   completionHandler:^(NSDictionary * _Nonnull response, NSError * _Nonnull error) {
     //数据解析
}];
```  
NSNetService+Fragrans  
```
//检查网络状态
BOOL net = [NSNetService checkNetWork];
[NSNetService sharedInstance].networkChangeBlock = ^(FRGNetworkStatus status) {
  //实时监听网络状态
};
```
UITextField+Frafrans   
```
UITextField   *textField = [UITextField textFieldWithFrame:  CGRectMake(100, 100, 200, 30)  placeholder:@"测试"   font:@14 textColor:@3  delegate:self];
[self addSubview:textField];
[textField layerBorderColor:@9 width:1];
//设置placeholder颜色和字体
[textField placeholderColor:[UIColor redColor] placeholderFont:@14];
//限制最多可以输入的字符,并返回长度内字符串
[textField maxLength:10 textStringBlock:^(NSString * _Nonnull textString) {
    //返回长度内字符串
}];
```  
效果  
![textfield_01](https://github.com/chadhea/Fragrans_image/blob/master/UITextField/textfield_01.gif)  
UIView+Fragrans  
```
UIView   *view = [UIView viewWithFrame:CGRectMake(100, 100, 100, 100)   backgroundColor:@9 tap:^(id  _Nonnull sender) {
   //点击事件
}];
[self addSubview:view];
//设置上边圆角
[view setCornerWithTop:20];
//设置渐变色
view.backgroundColor = [UIColor gradientForLeftToRightFromColor:[UIColor cyanColor]   toColor:[UIColor blueColor] width:50];
```
效果  
![uiview_02](https://github.com/chadhea/Fragrans_image/blob/master/UIView/uiview_02.png)  
```
- (void)drawRect:(CGRect)rect {
//drawRect重绘
[UIView drawLinePointArray:  @[frg_kValueWithPoint(100, 300),frg_kValueWithPoint(200, 300),frg_kValueWithPoint(200, 200),frg_kValueWithPoint(100, 300)]   lineWidth:3 strokeColor:[UIColor yellowColor]   fillColor:[UIColor gradientForLeftToRightFromColor:[UIColor cyanColor]   toColor:[UIColor redColor] width:100]];
}
```  
效果  
![uiview_03](https://github.com/chadhea/Fragrans_image/blob/master/UIView/uiview_03.png)  
```  
- (void)drawRect:(CGRect)rect {
[UIView drawCurveCenter:CGPointMake(200, 200)   radius:60 startAngle:0 endAngle:M_PI clockwise:1 lineWidth:40   lineColor:[UIColor gradientForTopToBottomFromColor:[UIColor blueColor]   toColor:[UIColor magentaColor] height:15] round:YES];
}
```  
效果  
![uiview_04](https://github.com/chadhea/Fragrans_image/blob/master/UIView/uiview_04.png)  
UILabel+Fragrans  
```
UILabel    *label = [UILabel labelWithFrame:CGRectMake(100, 100, 100, 100) text:@"测试\n换行"   font:@20 textColor:@3 backgroundColor:@"f" textAlignment:NSTextAlignmentCenter   tap:^(id  _Nonnull sender) {
    //点击事件
}];
[self addSubview:label];
//描边颜色、描边宽度及圆角角度
[label layerBorderColor:@9 width:3 cornerRadius:10];
//设置行间距和字间距
[label lineSpacing:20 wordSpacing:6];
```
效果  
![uilabel_01](https://github.com/chadhea/Fragrans_image/blob/master/UILabel/uilabel_01.png)  

UIButton+Fragrans  
```
UIButton  *button = [UIButton buttonWithCenter:CGPointMake(100, 100)   bounds:CGRectMake(0, 0, 150, 100) title:@"测试" font:@"15" titleColor:[UIColor redColor]   backgroundColor:@"e" target:self action:@selector(ceshiclick)];
[self addSubview:button];
//设置图片
[button normalImage:@"ceshi_normal" selectImage:@"ceshi_select"];
//设置button的titleLabel和imageView的布局样式，及间距
//FRGButtonEdgeInsetsStyleTop、Bottom、Left、Right、Center
[button layoutButtonWithEdgeInsetsStyle:FRGButtonEdgeInsetsStyleCenter imageTitleSpace:10];
```  
效果  
![button_top](https://github.com/chadhea/Fragrans_image/blob/master/UIButton/button_top.png)![button_bottom](https://github.com/chadhea/Fragrans_image/blob/master/UIButton/button_bottom.png)![button_left](https://github.com/chadhea/Fragrans_image/blob/master/UIButton/button_left.png)![button_right](https://github.com/chadhea/Fragrans_image/blob/master/UIButton/button_right.png)![button_center](https://github.com/chadhea/Fragrans_image/blob/master/UIButton/button_center.png)  
UIDevice+Fragrans  
```
[UIDevice getDeviceName];//获取设备型号  
[UIDevice getDeviceStringName];//获取原装的设备名称  
[UIDevice getIPAddress];//获取设备当前网络IP地址  
[UIDevice getIPAddresses];//获取所有相关IP信息  
[UIDevice isIpv6];//判断当前网络是否为ipv6  
[UIDevice getWANIPAddress];//获取外网地址,获取失败返回内网地址  
[UIDevice getDeviceUUID];//获取UUID  
[UIDevice getIDFA];//获取广告标识符  
[UIDevice systemVersion];//系统版本  
[UIDevice systemVersion_iOS_12_AndLater];//判断系统版本  
[UIDevice batteryLevel];//电量  
[UIDevice getSystemUptime];//系统上次启动时间  
[UIDevice getCPUCount];//获取CPU总数  
[UIDevice getCPUUsage];//CPU使用总比例  
[UIDevice getPerCPUUsage];//每个CPU使用比例  
[UIDevice totalDiskSpace];//获取总磁盘空间  
[UIDevice freeDiskSpace];//获取剩余磁盘空间  
[UIDevice totalMemorySpace];//获取系统总内存空间  
[UIDevice cpuFrequency];//CPU使用频率  
...
```  
NSFileManager+Fragrans  
```
[NSFileManager homeDirectoryPath];//获取Directory的路径  
[NSFileManager removeFile:@"xx"];//删除一个文件  
[NSFileManager createDirectory:@"xx"];//创建文件夹  
[NSFileManager copyResourceFileToCachesDirectory:@"xx"];//拷贝资源目录文件到caches目录  
[NSFileManager saveImageToDirectoryPath:@"xx" image:[UIImage imageNamed:@"ceshi"] imageName:@"ceshi" imageType:@"png"];//存储图片到指定的目录下  
[NSFileManager loadResourceByDirectoryPath:@"xx"];//获取指定目录下的资源  
[NSFileManager fileSizeAtPath:@"xx"];//获取文件或者文件夹占用空间（单位跟随文件大小变化）  
...
```  
UIPageControl+Fragrans  
```
UIPageControl   *pageControl = [UIPageControl pageControlWithFrame:CGRectMake(30, 100, 200, 30)   numberOfPages:10 currentPage:3 pageIndicatorTintColor:@8 currentPageIndicatorTintColor:@"eb3223"   target:self action:@selector(pageEvent:)];
pageControl.backgroundColor = [UIColor colorWithHexString:@"e"];
[self addSubview:pageControl];
```  
效果  
![pageControl_01](https://github.com/chadhea/Fragrans_image/blob/master/UIPageControl/pageControl_01.png)  

NSString+Fragrans  
```
//判断字符串是否符合要求。比如是否为手机号、邮箱、身份证等，如：
NSString   *str = @"xxx@163.com";
[str isEmailValidate];//是否为邮箱
//对字符串进行加密和解密,如：
[NSString encrypt_md5With:@"xxx"];//md5加密
NSString *key = @"key";//加密解密的key
NSString *jiami_str = [NSString  encryptAESWithString:@"xxx" secretKey:key];//AES加密
[NSString decryptAESWithString:jiami_str secretKey:key];//AES解密,返回原字符串
//过滤特殊的字符
[NSString filterHTML:@"xxx"];//去除html标签对
[NSString filterEmoji:@"xxx"];//去除emoji表情
```   
UISlider+Fragrans  
```
UISlider   *slider = [UISlider sliderWithFrame:CGRectMake(100, 100, 100, 30)   value:50 minimumValue:0 maximumValue:100 thumbTintColor:[UIColor blueColor] minimumTrackTintColor:[UIColor cyanColor]   maximumTrackTintColor:[UIColor redColor] target:self action:@selector(sliderEvent:)];
[self addSubview:slider];
```  
效果  
![slider_01](https://github.com/chadhea/Fragrans_image/blob/master/UISlider/slider_02.png)  

UISwitch+Fragrans  
```
UISwitch   *frg_switch = [UISwitch switchWithStarPoint:CGPointMake(100, 100)   thumbTintColor:[UIColor greenColor] onTintColor:[UIColor yellowColor] tintColor:[UIColor magentaColor]   target:self action:@selector(switchEvent:)];
[self addSubview:frg_switch];
```  
效果  
![switch_01](https://github.com/chadhea/Fragrans_image/blob/master/UISwitch/switch_01.gif)  
NSDateFormatter+Fragrans  
```
[NSDateFormatter getCurrentTimeStamp];//获取当前系统时间戳
NSString   *sp = [NSDateFormatter timeStampWithTime:@"2019-01-01 06:00:00"   formatter:@"yyyy-MM-dd HH:mm:ss"];//时间转时间戳
[NSDateFormatter timeWithTimeStamp:sp formatter:@"yyyy-MM-dd HH:mm:ss"];////时间戳转时间 + 格式
[NSDateFormatter timeWithDate:[NSDate date] format:@"yyyy-MM-dd"];//时间转化
    
//快速获取固定格式时间
[NSDateFormatter currentTime];//获取当前时间（24小时
[NSDateFormatter timeShangXiaWu];//获取当前时间（上午+下午）
[NSDateFormatter timeAM_PM];//获取当前时间（AM+PM）
[NSDateFormatter timeYMD];//获取当前时间（yyyy-MM-dd）
[NSDateFormatter timeYMD_Hms];//获取当前时间（yyyy-MM-dd hh:mm:ss）
[NSDateFormatter timeYMD_Hms_S];//获取当前时间（yyyy-MM-dd hh:mm:ss.SSS）
[NSDateFormatter currentWeekTime];//获取当前星期
[NSDateFormatter currentHourTime];//获取当前小时
[NSDateFormatter currentDataTime];//获取当前几号
```  
UITextView+Fragrans  
```
UITextView   *textView = [UITextView textViewWithFrame:CGRectMake(30, 100, 160, 60)   text:@"" font:@15 textColor:@3 backgroundColor:@"e" delegate:self];
[self addSubview:textView];
//设置placeholder
[textView placeholder:@"测试"];
- (void)textViewDidChange:(UITextView *)textView {
     //设置最大可输入长度，并返回长度内字符串
    NSString  *str = [textView frg_textViewDidChangeWithMaxLength:10];
}
```  
效果  
![textview_01](https://github.com/chadhea/Fragrans_image/blob/master/UITextView/textview_01.gif)  
UIScrollView+Fragrans  
```
UIScrollView   *scroll = [UIScrollView scrollViewWithFrame:CGRectMake(10, 100, [UIScreen screenWidth] - 20, 80) contentSize:CGSizeZero backgroundColor:@"c" showsScrollIndicator:NO bounces:YES delegate:self];
[self addSubview:scroll];
//scroll上添加图片,contentSize属性自动适应
[scroll addimages:@[@"ceshi_normal",@"ceshi_normal",@"ceshi_normal",@"ceshi_normal",@"ceshi_normal"]   starPoint:CGPointMake(10, 10) interval:10 direction:Frg_ScrollViewAddImageDirectionType_Horizontal   taps:^(id  _Nonnull sender, NSInteger index) {
   //每张图片的点击事件
        
}];
```  
效果  
![scroll_01](https://github.com/chadhea/Fragrans_image/blob/master/UIScrollView/scroll_01.gif)  






