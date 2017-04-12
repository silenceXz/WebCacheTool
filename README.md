# 网页缓存

下载代码并导入项目中，然后在使用的地方引入#import "CacheFileManagerTool.h"即可。

比如加载网页，需要知道网页地址self.urlPath，先判断是否有缓存，没有就进行网络加载并写入缓存，如果有就加载缓存文件。

NSURL *url = [NSURL URLWithString:self.urlPath];

// 如果有缓存，那么就从缓存中取得
NSString *htmlString = [CacheFileManagerTool readFromCache:self.urlPath];
if(!(htmlString == nil || [htmlString isEqualToString:@""])){
    
    [self.webHtml loadHTMLString:htmlString baseURL:url];
    
}else{
    
    [self.webHtml loadRequest:[NSURLRequest requestWithURL:url]];
}
