vue3中在父子组件传值时，子组件使用父组件传过来的值，出现了unknown的错误。
百度查询了半天，才知道是因为接收类型只为数组，并没有确定指向具体结构，就
会出现unknown的错误。解决方法：
``` vue
const getProps = defineProps({
     mytitle:{
         type:Array as () => Array<string>,//string可以为自己定义的接口
     }
})
```