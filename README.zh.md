<div align="center">
	<br />
	<br />
	<img src="./assets/logo.png" alt="Create Custom Symbols LOGO" width="160" height="160">
  <p>
		<a href="./README.md">English</a> • 
    <a href="#常见问题">常见问题</a> • 
		<a target="_blank" href="https://wangchujiang.com/#/contact">联系&支持</a>
  </p>
	<h1>Create Custom Symbols</h1>
  <!--rehype:style=border: 0;-->
  <p>
    <a target="_blank" href="https://apps.apple.com/app/create-custom-symbols/id6476924627" title="Create Custom Symbols AppStore"><img alt="Create Custom Symbols AppStore" src="https://tools.applemediaservices.com/api/badges/download-on-the-mac-app-store/black/en-us?size=250x83&amp;releaseDate=1705968000" height="51"></a>
  </p>
</div>

一个工具，能够将任意 SVG 图标转换为[自定义的 SF 符号](https://developer.apple.com/documentation/uikit/uiimage/creating_custom_symbol_images_for_your_app)。您可以将定制的 SF 符号导入 Xcode，并在任何基于 UIKit 或 SwiftUI 的项目中使用。

![RegexMate screenshots-1-cn](./assets/screenshots-1-cn.png)

通过拖放，将任何 SVG 图标轻松转换为可在 Xcode 中使用的 SF 符号文件，快速创建 SF 符号文件。

![RegexMate screenshots-2-cn](./assets/screenshots-2-cn.png)

支持批量导入 SVG 图标，并批量生成 SF 符号图标

![RegexMate screenshots-3-cn](./assets/screenshots-3-cn.png)

![RegexMate screenshots-4-cn](./assets/screenshots-4-cn.png)

### 常见问题

#### 如何在 SwiftUI 中使用您的自定义 SF 符号？

```swift
// Your custom symbol at Medium scale, Regular weight
Image("myCustomSymbolName")

// Your custom symbol at large scale, 21pt font and Heavy weight
Image("myCustomSymbolName")
    .imageScale(.large)
    .font(Font.system(size: 21, weight: .heavy))
```

您还可以在一些文本旁边显示自定义符号。

```swift
VStack {
    (Text("Some Text ")
        + Text(Image("myCustomSymbolName"))
        + Text(" more text")).imageScale(.large)
}
```

#### 如何在 UIKit 中使用您的自定义 SF 符号？

```swift
let customSymbol:UIImage? = UIImage(named: "MyCustomSymbolName")?
    .applyingSymbolConfiguration(
        UIImage.SymbolConfiguration(
            pointSize: 17,
            weight: .semibold,
            scale: .large
        )
    )
```

#### 如何在 AppKit 中使用您的自定义 SF 符号？

```swift
let customSymbol:NSImage? = NSImage(named: "MyCustomSymbolName")?
    .withSymbolConfiguration(
        NSImage.SymbolConfiguration(
            pointSize: 24,
            weight: .bold,
            scale: .large
        )
    )
```

为符号图像应用特定外观

```swift
var configuration = NSImage.SymbolConfiguration(paletteColors: [.systemTeal, .systemGray])
configuration = config.applying(.init(textStyle: .title1))
imageView.symbolConfiguration = config
```

#### 如何在 UIKit 中使用您的自定义 SF 符号？

```swift
// Create a system symbol image.
let image = UIImage(systemName: "multiply.circle.fill")                  

// Create a custom symbol image using an asset in an asset catalog in Xcode.
let image = UIImage(named: "custom.multiply.circle")
```

#### 如何将自定义 SF 符号添加到字符串中？

```swift
Text("使用 \(Image("myCustomSymbolName")) 裁剪图像")
```

#### 如何定义多彩 SF 符号？

目前暂时不支持，根据[官方文档](https://developer.apple.com/documentation/uikit/uiimage/creating_custom_symbol_images_for_your_app)手动去添加样式，仍然在未来尝试支持它

```html
<style>
  .multicolor-0:systemBlueColor { fill:#007AFF; opacity:1.0 }
  .multicolor-1:white { fill:#FFFFFF; opacity:1.0 }
  .multicolor-2:tintColor { fill:#007AFF; opacity:1.0 }
  .hierarchical-0:tertiary { fill:#8E8E8E }
  .hierarchical-1:primary { fill:#212121 }
</style>

<g id="Symbols">
  <!-- 包含三种形状的变体，具有多色和分层注释。 -->
  <g id="Regular-M" transform="matrix(1 0 0 1 2853.78 1556)">
      <!-- 形状位于第一个多色图层中，其填充颜色为 systemBlueColor。它也位于分层渲染的第一个图层中，层级为一级。-->
      <path class="multicolor-0:systemBlueColor hierarchical-1:primary" d="...">
  
      <!-- 两个额外的形状。 -->
      <path class="multicolor-1:white hierarchical-1:primary" d="...">
      <path class="multicolor-2:tintColor hierarchical-0:tertiary" d="...">
    </g>
</g>
```

### [更多问题...](https://github.com/jaywcjlove/create-custom-symbols/issues)