# rem.scss
SCSS Rem solution


### 实现原理

我们知道，以Chorme为例，浏览器的html默认字体为16px,因此，px和rem存在如下对应关系：

> px/font-size = rem

```
    |  px  |     rem       |
    ------------------------
    |  12  | 12/16 = .75   |
    |  14  | 14/16 = .875  |
    |  16  | 16/16 = 1     |
    |  18  | 18/16 = 1.125 |
    |  20  | 20/16 = 1.25  |
    |  24  | 24/16 = 1.5   |
    |  30  | 30/16 = 1.875 |
    |  36  | 36/16 = 2.25  |
    |  42  | 42/16 = 2.625 |
    |  48  | 48/16 = 3     |
    ------------------------
```

其实还有个更好的，那就是设置html的字体大小为10px：

```
	|  px  |     rem       |
    ------------------------
    |  12  | 12/10 =  1.2  |
    |  14  | 14/10 =  1.4  |
    |  16  | 16/10 =  1.6  |
    |  18  | 18/10 =  1.8  |
    |  20  | 20/10 =  2.0  |
    |  24  | 24/10 =  2.4  |
    |  30  | 30/10 =  3.0  |
    |  36  | 36/10 =  3.6  |
    |  42  | 42/10 =  4.2  |
    |  48  | 48/10 =  4.8  |
    ------------------------
```
我们通常使用rem时，切设计稿的时候就会量出资源的宽高，再把宽高转换成rem单位，使用了sass之后呢，这一步就可以使用函数或者@mixin了。

rem.scss就是把这些操作收集成为一个集合。

### 用法：

`pxToRem`:

```
	//scss
    .header{
    	font-size: pxToRem(12px);
    }

    //css
    header{
    	font-size:0.75rem;
    }
```

`mulpxToRem`:

```
	//scss
	.test{
		margin: mulpxToRem(10px 20px);
	}

	//css
	.test{
		margin: .625rem 1.25rem;
	}
```

`remMixin`:
@mixin用法

```
	//scss
	.testMulRemMixin{
		include remMixin(margin,10px 20px);
	}

	//css
	.testMulRemMixin{
		margin:.625rem 1.25rem
	}
```


