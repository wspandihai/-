seajs流程初探.  seajs.use方法作为整个seajs的入口,在这个方法中生成一个匿名的模块并且绑定了回调函数,开始load.在load方法中获得当前use匿名模块的依赖项,加入到此依赖项的_wait列表中,开始加载依赖项,当所有依赖项都加载完毕loaded,开始自己的onload方法,在里面执行回调,在这个回调方法中执行他各个依赖项的exec方法,最后将依赖项返回的接口,传入回调中执行callback方法.



requirejs相比较seajs,requirejs的入口比较统一（我是觉得比较统一,也有人说他的require方法职责过于重,职责不清.）。
require在加载完一个依赖模块之后如果发现这个模块存在另外的依赖模块会立刻去请求,当所有的依赖模块都enable了之后也会立刻回调。