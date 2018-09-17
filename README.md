[模仿](https://blog.csdn.net/tangxiujiang/article/details/80157315)

**效果图**

![](/mdImg/star组件.png)

**引用组件**

```html
<!-- 商家评星 -->
<div class="star-wrapper">
  <star :rating='businessData.rating' :size='48'></star>
</div>
<script>
import star from './star/Star'
export default {
  components: { star }
}
</script>
```

**设计知识**

[父组件传递数据给子组件](https://bryantout.github.io/2018/08/30/vue%E7%9A%84%E7%BB%84%E4%BB%B6/)

[vue过渡&动画](https://bryantout.github.io/2018/08/29/vue%E8%BF%87%E6%B8%A1%E5%8A%A8%E7%94%BB/)