Title: git 源码分析(1)
Date: 2016-01-17 21:54

    为了简单起见，我们这里分析Linus Torvalds初次commit版本。
    commit e83c5163316f89bfbde7d9ab23ca2e25604af290
    Author: Linus Torvalds <torvalds@ppc970.osdl.org>
    Date:   Thu Apr 7 15:13:13 2005 -0700

### 1. read-cache.c
<img src="./image/note/git_verify_hdr.png" width="550" height="530">
    
```
struct cache_header {
	unsigned int signature;
	unsigned int version;
	unsigned int entries;
	unsigned char sha1[20];
};
```
   
    验证 cache_header
    第200行，检查cache_header结构体中sha1成员变量的值和现在计算出的sha1值是否相等。
    如果不等，则cache_header检验失败。
    那么这个sha1的值是怎么计算出来的呢？这里分为两步，第一步：计算cache_header前三个
    成员变量值的sha1，其中offsetof取得成员变量sha1的偏移量。第二部：计算index文件中
    除去cache_header外的内容的sha1。 总的sha1通过SHA1_Final函数保存到sha1中。

