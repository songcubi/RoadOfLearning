##  MVVM模式

- vue使用的是MVVM模式。

- 没有完全遵循 [MVVM 模型](https://zh.wikipedia.org/wiki/MVVM)

- MVC模式：model-view-control。

- MVVM模式：model-view-viewModel。
	>- 可以看出MVVM使用viewModel代替了MVC的control，而vue也正是在viewModel中起作用的。
	>- viewModel：负责业务的逻辑处理，对数据进行加工后交给视图处理。

## 虚拟DOM
- vue和react都是使用到虚拟DOM实现快速渲染。
>若一次操作中有10次更新DOM的动作，虚拟DOM不会立即操作DOM，而是将这10次更新的diff内容保存到本地一个JS对象中，最终将这个JS对象一次性attch到DOM树上，再进行后续操作，避免大量无谓的计算量。所以，用JS对象模拟DOM节点的好处是，页面的更新可以先全部反映在JS对象(虚拟DOM)上，操作内存中的JS对象的速度显然要更快，等更新完成后，再将最终的JS对象映射成真实的DOM，交由浏览器去绘制。
