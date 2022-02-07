## 常见问题指南
- [ScrollView无法滚动](#ScrollView无法滚动)
- [三端统一RN坑盘点](#三端统一RN坑盘点)
- [RNstyle注意点](#RNstyle注意点)

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

## 三端统一RN坑盘点

> 在样式方面，RN是弱势方，所以在写样式尽量以RN为准，比如不支持css3的新特性，border-style等等。还有一个重点不支持样式嵌套哦，如下：

```
// RN不支持
.main {
  height: 200px;
  .view {
    width: 200px;
  }
}
// 需要拆分
.main {
  height: 200px;
  
}
.view {
   width: 200px;
}

```

## RNstyle注意点

> RN的style某些数值不能写单位px, 如 <View style={{ width: "20px" }}/> RN不支持，如果不写px H5和小程序就不行了，建议使用样式，如果非常情况下自己做个平台判断封装方法

```
// 比较戳的一个方式，哈哈
export const stylePX = (px: number) => {
    if (process.env.TARO_ENV === 'rn') {
        return px
    }
    return `${px}px`
}
```

> RN不支持border: 1px red solid;  只能border-color: red;这样，因为RN StyleSheet里面不支持，taro仅仅只是把-改成驼峰命名，taro RN推出比较晚，需要慢慢完善，比如background-image, 背景渐变都不支持(可以使用第三方RN组件走原生的方式实现react-native-linear-gradient)



