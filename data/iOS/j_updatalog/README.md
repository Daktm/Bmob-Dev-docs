v1.7.0   2016年4月22日
1.恢复BmobProFile文件下载的功能
2.恢复云端代码同步接口（请在子线程使用），新增+(id)callFunction:(NSString *)function withParameters:(NSDictionary *)parameters error:(NSError **)error;返回错误信息
3.Bmob类新增设置文件上传的授权时间和分片大小
4.BmobInstallation类去掉currentInstallation(命名让人误会)，用installation代替(单纯创建一个BmobInstallation对象).

v1.6.9   2016年4月14日
1.文件服务更换为CDN上传,废除新旧文件上传服务
2.新增文件批量删除接口
3.去掉调用云端代码同步的方法
4.BmobUser 设置用户名变为setUsername:(NSString *)username
5.更换网络请求库为NSURLSession
6.修复设置超时时间没有反馈的bug
7.修复某些回调不在主线程的问题

v1.6.8   2016年3月31日
1.修复上一个版本用户可能无法更新资料和实时监控的问题

v1.6.7   2016年3月18日
1.修复注销登录后的bug
2.修复请求完成后，偶然会崩溃的的bug

v1.6.6   2015年12月23日
1.添加封装的复合查询方法
2.原子计数器支持浮点数 3.修复网络环境较差时出现崩溃bug 4.增加异步获取服务器时间的方法 

v1.6.5   2015年10月08日
1.支持bitcode操作； 2.添加从字典初始化BmobObject方法； 3.添加单独修改JSON对象某个key-value对的功能。 

v1.6.4   2015年8月27日
修改注册后没返回objectId的问题

v1.6.3   2015年8月24日
1.添加根据旧密码修改新密码接口；
2.添加手机验证码注册时可同时添加新密码或者是其它user列的信息接口；
3.修改上传多个图片时偶然冲突导致上传失败的bug。

v1.6.2   2015年8月18日
1.修复缩略图无法返回的问题
2.修复上传图片时，文件路径有误时应用出错的问题

v1.6.1   2015年7月27日
1.修复使用账号密码注册时无法上传手机号的bug；
2.开放获取表结构的接口。

v1.6.0   2015年7月14日
1.文件上传兼容旧文件系统
1）修改上传文件接口
2）添加获取已经上传文件访问url接口
3）删除已上传文件接口
2.修复子类化bug
3.添加数组查询接口
4.修复文件上传下载接口如果传空block会报错的bug

v1.5.9   2015年7月01日
1.提供修改超时间接口
2.修复子类化bug
3.修复实时监听bug
4.提供自定义短信内容发送功能

v1.5.8   2015年6月12日
1.添加短信功能
2.添加BmobObject子类化功能
3.修复缓存查询部分bug
4.修复云端代码无法同步bug
5.第三方登录添加微信登录

v1.5.7   2015年5月14日
1.添加BQL查询功能
2.开放模糊查询功能 

v1.5.6   2015年5月04日
1.修改文件操作头文件部分注释；
2.修复模拟器下有时无法上传文件的问题。 
	
v1.5.5   2015年4月24日
1.增加统计查询方法
2.修复部分bug


v1.5.4   2015年4月07日
1.增加批量上传方法
BmobFile
+(void)filesUploadBatchWithDataArray:(NSArray *)dataArray
                       progressBlock:(BmobFileBatchProgressBlock)progress
                         resultBlock:(BmobFileBatchResultBlock)block;
                         
BmobFilePro
+(void)uploadFilesWithDatas:(NSArray *)dataArray
                resultBlock:(BmobBatchFileUploadResultBlock)block
                   progress:(BmobIndexAndProgressBlock)progress;
2.修复其他问题

v1.5.3   2015年3月05日
1.修复蜂窝网络下可能会出现的使用新版文件上传文件，上传不了的问题
2.修复在某些情况下用户可能无法更新表内容的问题

v1.5.2   2015年2月07日
1.兼容1.5.1跟1.5.1之前的版本，即可以监听到通知再调用请求方法，也可以直接调用请求方法

v1.5.1   2015年1月22日
1.添加初始化完成后通知kBmobInitSuccessNotification，kBmobInitFailNotification 2.修改更新用户后本地用户可能会为空的问题 注意：
1.5.0之后的版本新增了加密功能，所以在还没初始化完成的时候请求接口会出现问题。
开发者可以监听此通知，获取成功通知的时候再进行其他接口的请求。 最后更新于2015-01-23 

v1.5.0   2015年1月19日
1.增加数据加密，建议使用新版本
2.BmobProFile添加开启验证后得到的url方法
3.在进入前台是需要调用
- (void)applicationWillEnterForeground:(UIApplication *)application
{
    [Bmob activateSDK];
}
注： 1.如果下载了1月17号版本的，可以用这个版本进行替换; 

v1.4.13   2015年1月05日
1.新增文件管理类BmobProFile，提供多种上传方法等。
2.需要添加libsqlite3.dylib,AVFoundation.framework、MediaPlayer.framework依赖库 点这里查看详细文档

v1.4.12   2014年12月25日
1.修复无网络时获取服务器时间出现的问题

v1.4.11   2014年12月17日
1.修改安全认证方法，注册方式可换回原来的方法,建议使用新版本
 NSString *appKey = @"xxxx";
[Bmob registerWithAppKey:appKey];
2.修复云端代码同步方法与异步方法数据格式不一样的问题

v1.4.10   2014年12月09日
1.增加安全认证的功能，注册应用方式修改为
NSString *appKey = @"xxxx";
#if DEBUG  [Bmob registerWithAppKey:appKey]; #else
 [Bmob registerWithAppKeyReleaseMode:appKey];
#endif
2.文件分片上传功能新增进度的方法。进度的范围为（0.0f-1.0f）
3.新增批量上传的方法
4.BmobQuery新增-(void)whereKeySExists:(NSArray *)keys;
和-(void)whereKeysDoesNotExist:(NSArray *)keys; 方法

v1.4.9   2014年10月20日
1.修复openudid冲突的问题

v1.4.8   2014年10月11日
1.修复用户更新函数在iOS6下可能出现的崩溃问题
2.修复已知的查询函数可能进入不了block的问题

v1.4.7   2014年10月10日
1.修复已知的云端代码的问题

v1.4.6   2014年9月22日
1.修复本地缓存用户，更新后本地基本数据类型不一致的问题

v1.4.5   2014年9月17日
修复一些问题及优化结构

v1.4.4   2014年9月12日
修复v1.4.3的一些问题 

v1.4.3   2014年9月04日
1.批量添加批量更新，也能增加特殊类型

v1.4.2   2014年8月20日
1.BmobUser 添加获取邮箱是否已验证的方法
2.修复BmobUser有可能更新不成功的问题

v1.4.1   2014年8月05日
BmobUser类增加：
1.手机QQ，新浪微博账号注册登录Bmob的功能
2.关联QQ账号，微博账号功能
3.提供取消关联的功能 

v1.4.0_Beta   2014年7月18日
1、增加数据实时功能，提供多种监听表变化的方法。
2、增加BmobEvent类别，监听事件后，开发者可在代理函数里进行操作。
3、依赖库需要添加多libicucore.dylib

v1.3.15_Beta   2014年7月17日
1、BmobQuery的- (void)getObjectInBackgroundWithId:(NSString *)objectId
                              block:(BmobObjectResultBlock)block
也支持-(void)includeKey:(NSString *)key跟-(void)selectKeys:(NSArray*)keys了

v1.3.14_Beta   2014年7月14日
1、修复2G网络下查询可能会crash的问题

v1.3.13_Beta   2014年6月18日
1、修正一些bug
2、修正缓存查询可能存在的问题

v1.3.12_Beta   2014年6月11日
1、BmobQuery新增自定义查询条件接口：-(void)queryWithAllConstraint:(NSDictionary*)conDictionary;
2、BmobQuery新增取消接口

v1.3.11_Beta   2014年5月28日
1、修复更新可能不成功的问题

v1.3.10_Beta   2014年5月27日
1、BmobFile类添加分片上传的方法
2、添加BmobACL权限和BmobRole角色管理类
3、添加BmobImage图像处理类，提供多种方法处理图像

v1.3.9_Beta   2014年5月21日
1、修复user表有关联关系，用户登录后更新不成功的问题

v1.3.8_Beta   2014年5月16日
1、修复云端代码同步没返回的bug
2、增加文件上传进度和取消上传函数
3、修复添加SDK出现多个警告的问题

v1.3.7_Beta   2014年4月30日
1、增加BmobInstallation类，注册需要推送的设备。
2、增加BmobPush功能模块，可进行自定义推送。

v1.3.6_Beta   2014年4月23日
1、BmobUser增加邮箱验证接口，只有在web端应用设置里开启邮箱验证才有效
2、增加BmobObjectBatch类，批量修改数据

v1.3.5_Beta   2014年4月18日
1、添加x86_64位、arm64架构
2、添加指针类型，和relation类型
3、添加BmobObject对象列为Number时，可进行原子增加或减少的功能
4、添加BmobRelation类，为BmobObject之类关联关系
5、BmobQuery新增查询约束条件
- (void)includeKey:(NSString *)key;
- (void)whereKey:(NSString *)key matchesQuery:(BmobQuery *)query;
- (void)whereKey:(NSString *)key doesNotMatchQuery:(BmobQuery *)query;
- (void)whereObjectKey:(NSString *)key relatedTo:(BmobObject*)object;
6、去掉BmobQuery查询中关于字符串的查询条件
-(void)whereKey:(NSString*)key matchesWithRegex:(NSString*)regex
-(void)whereKey:(NSString *)key startWithString:(NSString*)start
-(void)whereKey:(NSString *)key endWithString:(NSString*)end

v1.3.4_Beta   2014年4月10日
1、Bmob.h 引入头文件,方便调用

v1.3.3_Beta   2014年4月08日
1、增加合成查询，并操作跟或操作

v1.3.2_Beta   2014年4月06日
1、修复[BmobUser getCurrentObject]与 之前版本不兼容的问题

v1.3.1_Beta   2014年4月04日
1、修复BmobFile url的相关bug
2、增加BmobQuery约束条件： - (void)selectKeys:(NSArray*)keys; - (void)whereKeyExists:(NSString *)key; - (void)whereKeyDoesNotExist:(NSString *)key; 

v1.3.0_Beta   2014年3月27日
1、修复BmobUser无法重置密码的bug 2、修复BmobFile保存成功后，返回完整地址 

v1.2.91_Beta   2014年3月21日
1、修正一些bug

v1.2.9_Beta   2014年3月18日
1、Bmob类增加获取服务器时间接口

v1.2.8_Beta   2014年3月12日
1、修复登陆失败后没返回错误信息
2、加入合作伙伴华为PUSH_SDK包

v1.2.7_Beta   2014年3月05日
1、修复上传文件失败的bug
2、修复BmobObject 函数-(void)setObject:(id)obj forKey:(NSString*)aKey;obj为nil时，crash的问题
3、修复某些字符无法保存的问题
4、修复BmobFile 路径没有文件时crash的问题
5、BmobFile增加saveInBackground方法

v1.2.6_Beta   2014年3月04日
1、修复添加NSDate类型失败的问题
2、BmobObject类添加-(void)saveAllWithDictionary:(NSDictionary*)dic;方法，支持批量添加数据

v1.2.5_Beta   2014年2月25日
1.修复在非主线程block没回调的问题

v1.2.4_Beta   2014年2月24日
1.使用自带访问网络的类替代部分第三方库 2.saveInBackground 添加返回数据信息 

v1.2.3_Beta   2014年2月14日
1.修复BmobUser 更新属性后本地没更新的bug
2.修改地理位置查询，排序结果从近到远，而不是根据updateAt降序排序

v1.2.2_Beta   2014年2月12日
1.优化初始化函数

v1.2.1_Beta   2014年1月02日
1.新增云端代码功能
2.优化性能，减少冗余

v1.2.0_Beta   2013年12月02日
1.更改静态库为framework，减少体积
2.调整调用函数，更稳定更便捷
3.增加完善部分错误信息回调接口

v1.1.7_Beta   2013年11月27日
1.解决打包出现的一些问题 2.优化相关回调函数 

v1.1.6_Beta   2013年11月26日
1、增加稳定性，优化代码结构
2、BmobQuery增加查询用户函数+(BmobQuery*)queryForUser;
3、新增加密码重置功能
4、新增用户登陆功能，登陆成功返回个人信息
5、新增接口请求数据统计

v1.1.5_Beta   2013年11月06日
1、修复在循环中使用BmobQuery:- (void)getObjectInBackgroundWithId:(NSString *)objectId block:(BmobObjectResultBlock)block; 遇到的问题

v1.1.4_Beta   2013年10月29日
1、新增Count查询功能
2、新增地理位置查询功能
3、修改BmobGeo类初始化方法与web端显示不一致的问题

v1.1.3_Beta   2013年10月17日
1.修复BmobObject取特殊类型属性错误的bug
2.修复上传时会更新createdAt的问题

v1.1.2_Beta   2013年10月11日
1、修复BmobObject类updatedAt、createdAt类型问题

v1.1.1_Beta   2013年10月09日
1、对网络传输的优化

v1.1.0_Beta   2013年9月22日
1、BmobFile类添加了初始化方法：-(id)initWithClassName:(NSString *)className withFileData:(NSData*)data;可以直接上传二进制数据
2、修复了BmobQuery类中- (void)findObjectsInBackgroundWithBlock:(BmobObjectArrayResultBlock)block;得到的数组中的对象不能更新的bug

