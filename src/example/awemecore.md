# Hopper使用举例：AwemeCore

## Hopper加载AwemeCore

* 输入文件：`AwemeCore`

然后把`AwemeCore`拖进`Hopper`

![hopper_load_awemecore](../assets/img/hopper_load_awemecore.png)

出现Loader弹框：

![hopper_loader_options](../assets/img/hopper_loader_options.png)

然后开始加载和分析：

* Loading Mach-O AArch64 file
  * Processing bindings
    * ![hopper_loading_processing_bindings](../assets/img/hopper_loading_processing_bindings.png)
  * Reading Objective-C
    * Reading Objective-C super refs
      * ![hopper_loading_reading_objc_super_refs](../assets/img/hopper_loading_reading_objc_super_refs.png)
    * Reading Objective-C class list
      * ![hopper_loading_reading_objc_class_list](../assets/img/hopper_loading_reading_objc_class_list.png)

加载完毕，进入主页面：

![hopper_awemecore_main_ui](../assets/img/hopper_awemecore_main_ui.png)

缺点：目前总体有点卡顿

### 分析代码逻辑

接下来，就是如何具体分析逻辑了

![hopper_awemecore_see_function](../assets/img/hopper_awemecore_see_function.png)

此处可以看到函数名：`awe_isBackground`

双击后，跳转到函数实现：

![hopper_awemecore_function_implementation](../assets/img/hopper_awemecore_function_implementation.png)

点击 尝试别人说的，切换到 伪代码 ObjC的

![hopper_awemecore_pseudo_code_mode](../assets/img/hopper_awemecore_pseudo_code_mode.png)

此处出现警告：

* No procedure at this address
  * ![hopper_awemecore_no_procedure_this_address](../assets/img/hopper_awemecore_no_procedure_this_address.png)

继续去找其他逻辑：比如，是否有越狱相关内容。

从左边的函数列表：

![hopper_left_function_list](../assets/img/hopper_left_function_list.png)

找找哪些和 启动相关的、初始化相关的

比如之前看到的，靠近entry的`AWELaunchMainPlaceholder`这种函数：

![hopper_function_entry_point](../assets/img/hopper_function_entry_point.png)

就很值得好好研究看看

另外继续研究越狱相关：

继续研究左边函数列表：

![hopper_left_function_more](../assets/img/hopper_left_function_more.png)

去试试，搜索`Find`->`Find`

![hopper_function_find_find](../assets/img/hopper_function_find_find.png)

越狱：`jailbreak`

* ![hopper_find_jailbreak](../assets/img/hopper_find_jailbreak.png)
  * 看看Type还有哪些类型
    * ![hopper_find_type_option](../assets/img/hopper_find_type_option.png)
  * 此处为了模糊搜索更多内容，所以取消勾选：`Case sensitive`
    * ![hopper_find_no_case_sensitive](../assets/img/hopper_find_no_case_sensitive.png)

开始搜索：

![hopper_find_searching](../assets/img/hopper_find_searching.png)

此处搜索了很多分钟，仍没有结束。

后来是，等待了2天多，依旧没结束，所以放弃。

尝试点击Cancel时，已无法点击。

索性强制退出：

![hopper_awemecore_force_quit](../assets/img/hopper_awemecore_force_quit.png)

![hopper_quit_report](../assets/img/hopper_quit_report.png)

->

* 目前的结论
  * Hopper对于（包含逻辑和内容很多的）大的二进制，基本上无法正常使用。
