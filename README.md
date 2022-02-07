## 常见问题指南
- [ScrollView无法滚动](#ScrollView无法滚动)


## ScrollView无法滚动

> app.less加入如下样式


```
page {
  height: 100%;
}
```

> SrollView外部用一个View包裹


```
.scroll-main {
    flex: 1;
    position: "relative";
}
.scroll {
    width: 100%;
    height: 100%;
    position: absolute;
    flex-direction: column;
}
<View className="scroll-main">
    <ScrollView className="scroll"></ScrollView>
</View>
```



