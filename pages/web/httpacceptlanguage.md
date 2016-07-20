##  浏览器怎么决定发送HTTP的Accept-Language请求头

不同的浏览器方式不同，比如IE是使用Windows default locale 来决定Accept-Language 属性的。

也有的浏览器根据自身的属性，如果你下载的是中文版的浏览器，那么默认的Accept-Language就是zh_CN.

这时可以设置相应的默认语言属性，比如FireFox，可以去 Tools > Options (Windows) or Firefox > Preferences (Mac OS X), and select Content (tab) > Languages > Choose (button). 选择Chinese(zh_CN)，就是相应的简体中文版。

比如Google Chrome，可以chrome://settings/ , 点Show advanced settings， 其中的Language选项，点击languages and input settings选择相应的语言即可。

** 注意: ** chrome Languages选项中当有多种语言时， 会把所有Accept-Language的语言都随着请求发送出去，可以把需要Accept-Language的语言放到第一位，可便于程序处理.
