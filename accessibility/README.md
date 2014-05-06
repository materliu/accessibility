# Basics about Accessibility

当你设计你的网站的时候，你一定要保证你的程序可以被任何的用户访问，即使是那些需要借助读屏软件等辅助设备的用户。为了做到这一点，你就必须保证使用的html标签是具有充分的语义化特征。尽可能保持html标签的结构简单可以在一定程度上实现语义化，但仅仅靠这些是无法达到高可用性的，即使html5引入了更多类似于header, section, sidebar, nav, footer这样高语义化的标签也力不从心。

为什么这么说，我们设想一下，你现在实现的是一个webApp，其中存在大量的js代码，动态的修改你的页面结构，那么最初优良设计的标签结构可能很快变得混乱不堪。那如何解决这个问题呢，这也就引出了我们下边要提到的WAI(web accessibility Initiative)和ARIA(Accessible Rich Internet Applications)标准。

WAI-ARIA标准的设计初衷是希望我们开发者在设计网站的时候能够加入更多的无障碍信息来帮助残障人士更好的获取我们页面的相关信息，ARIR中role， relationship， status， property的概念的使用，可以提供给读屏软件足够充分的信息来实现这一目的。

举例来说，你需要定义一个同时允许输入和下拉选择的组合下拉列表框，如果按照html4时代的写法，我们可能会像下边这样写：

```
<!-- 示例一 -->
<input class="combobox-input" type="text"/>
<ul class="chose-list">
    <li class="option">option1</li>
    <li class="option">option2</li>
</ul>
```

然后通过css和js的修饰来进行ul的显示隐藏，选择等， 这对于读屏软件及其不友好。

使用了ARIA就不一样了，下边是www.w3.org给出的一个标准示例, 我做了一些修改来使它更易于我们说明问题：

```
<!-- 示例二 -->
<input class="combobox-input"
       type="text"
       role="combobox"
       aria-activedescendant="option2"
       aria-autocomplete="list"
       aria-expanded="true"
       aria-label="Tag"
       aria-owns="chose-list"/>
<ul class="chose-list" id="chose-list" role="listbox">
    <li class="option" id="option1" role="option">option1</li>
    <li class="option" id="option2" role="option">option2</li>
</ul>
```

以下测试结果均在MAC平台下chrome中进行，使用voiceover读屏软件, 稍后如果有时间我会补齐国内读屏软件的测试情况，因为我用的英文版的系统，所以读屏也以英文为主。
在示例一中，我们将光标焦点定位到input元素内，会提示："edit text blank"中文就是"编辑文本空白" 对于盲人用户来说，完全不知道这里要做什么。
而在示例二中，则会提示："Tag combo box"中文则是"Tag组合框"，盲人用户就会知道这里是用来输入Tag的一个组合下拉列表框，

各项属性的意义：

aria-label和role是最好理解的，aria-label作为一个读屏提示存在，读屏软件会首先读label中的值，role则是提示当前标签所扮演的角色。html5规定，我们可以按照ARIA标准中的规定对html元素设定相关role和aria-*属性，在html4中则不支持这样做。同时html5为一些特定的元素隐式赋予了role属性，比如说html中的input type="checkbox"元素，默认就会有一个role="checkbox",对于这样的元素，我们要切记不要再画蛇添足或者弄巧成拙的非必要的修改其role属性。不仅仅是改变了其默认的语义含义，还有可能存在我们潜在难于发现的错误。但有些情况下又要具体分析，举例来说，有时候我们会使用a标签来模拟一个提交按钮，在提交的时候进行一些表单验证的工作。默认情况下，a标签的role属性是link，显然不适用于我们上边提到的这种使用场景，那就需要我们显式修改其role属性为button。role属性的修改必然不是随心所欲的，a标签就不适合做listbox，所以html5中也规定了某一个元素都可以被赋予哪些role属性，比如说a就只能被赋予：button, checkbox, link, menuitem, menuitemcheckbox, menuitemradio, tab, treeitem中的一种。html5规范中维护了这样一个清单，哪些元素有隐式的role属性，以及可以被显式修改的role属性的范围，可以参见： [http://www.w3.org/html/wg/drafts/html/master/dom.html#wai-aria](http://www.w3.org/html/wg/drafts/html/master/dom.html#wai-aria)

aria-autocomplete: 默认情况下autocomplete是设置为none的，这种情况下随着用户的输入，我们必须通过js显式地控制焦点将其聚焦到匹配到的list选项，

