#### 使用vite创建项目
1.create-vite-app  项目名称 -- --template vue(vue-ts)都只能创建vue3项目，并没有ts。

2.npm create vite-app 项目名称 -- --template vue(vue-ts)创建vue3(vue3+ts)项目。
#### 配置路由
安装：
``` tip 使用npm安装
npm install vue-router@4，
```
配置路由index.ts
``` vue
import { createRouter, createWebHistory, RouteRecordRaw } from 'vue-router'
const routes: Array<RouteRecordRaw> = [
  {
    path:'/',
    name:'Home',
    component: () => import('../views/MainView.vue'),
  }
]
const router = createRouter({
  history: createWebHistory(),
  routes
})
export default router
```
#### 配置vuex
安装：
``` tip 使用npm安装
npm install --save vuex@next
```
配置vuex index.ts
``` vue
import { createStore } from 'vuex'

export default createStore({
  modules: {
    demo1:{
      state: {
        str:'hello VueX',
      },
      getters:{
        getterStr:(state)=> state.str,
      },
      mutations: {
        mutationStr:(state,val)=>{
          state.str = val;
        }
      },
      actions: {
        async setValStr({state,commit},strIn){
          commit('mutationStr',strIn);
        },
      },
    }
  }
})
```
#### axios
安装：
``` tip
npm install axios
```
使用需要在main.ts的全局属性上挂载

#### elment-plus
安装：
``` tip
npm install element-plus --save
```
使用
``` vue
import ElementPlus from 'element-plus'
import 'element-plus/dist/index.css'
const app = createApp(App)
app.use(ElementPlus)
```
