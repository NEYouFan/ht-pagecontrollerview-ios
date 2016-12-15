HTPageControllerView
---
HTPageControllerView管理多个Controller，使得他们可以以整页的方式左右滚动。

![Mou icon](yx.gif)

特性
---
* 可配置在内存中Controller最大个数，自动删除和创建新的Controller
* 首次创建时，内部管理的Controller个数可配置，减轻初次创建时的消耗
* 在快速滑动Controller来不及显示时，可定制Controller的占位控件
* 接口类似UITableView，提供HTPageControllerViewDataSource和HTPageControllerViewDataDelegate

用法
---
HTPageControllerView使用类似于UITableView：

1. 创建HTPageControllerView

	```
	_pageControllerView = [[HTPageControllerView alloc] initWithFrame:CGRectMake(0, 0, 0, 0)];
    _pageControllerView.pageDataSource = self;
    _pageControllerView.pageDelegate = self;
    [self.view addSubView:_pageControllerView];
	```

2. 实现协议`HTPageControllerViewDataSource`

	```
	- (NSUInteger)numberOfControllersInPageControllerView
	{
    	return 4;
	}

	- (UIViewController*)pageControllerView:(HTPageControllerView*)pageControllerView viewControllerForIndex:(NSUInteger)index
	{
    	UIViewController *vc = [[TestPageViewController alloc] initWithNibName:nil bundle:nil withIndex:index];
    	return vc;
	}
	```
	
安装
---
###	CocoaPods
pod 'HTPageControllerView'


系统要求
---
iOS 7.0及以上

许可证
---
HTBadgeTextView使用MIT许可证，详情见LICENSE文件。
