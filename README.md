# FullScreen 全屏显示

代码示例：
```
<FullScreen />

<FullScreen :targetEle="targetEle" />
```

```javascript
import FullScreen from './FullScreen'

export default {
    components: {
        FullScreen
    },
    // 指定目标元素全屏，可以省略
    data () {
        return {
            targetEle: {},
        }
    },
    mounted () {
        this.targetEle = this.$refs.body.$el
    },
}
```

## API

参数 | 说明 | 类型 | 默认值
----|------|-----|------
iconStyle | 图标样式 | Object | {}
targetEle | 全屏的目标元素 | Object, HTMLElement | document.getElementById('blankLayout') \|\| document.documentElement
