<template>
  <el-row class="menu_page">
    <el-col>
      <el-menu
        active-text-color="#ffd04b"
        background-color="#918081"
        class="el-menu-vertical-demo"
        text-color="#fff"
      >
       <router-link to='/home'>
            <el-menu-item index='0'>
                <span slot="title">首页</span>
            </el-menu-item>
            <template v-for='item in items'>
                <el-sub-menu v-if='item.children' :index='item.path' :key="item.path">
                    <template #title>
                        <span slot="title">{{item.name}}</span>
                    </template>
                    <router-link v-for='(citem,cindex) in item.children' :to='citem.path' :key='cindex'>
                        <el-menu-item :index='citem.path'>
                            <span slot="title">{{citem.name}}</span>
                        </el-menu-item>
                    </router-link>
                </el-sub-menu>
            </template>
       </router-link>
      </el-menu>
    </el-col>
  </el-row>
</template>

<script>
export default {
    name:'left-menu',
    data(){
        return {
            items:[
            {
                name:'事务',
                path:'work',
                children:[
                    {path:'pay',name:'缴费'},
                    {path:'repair',name:'报修'},
                    {path:'complain',name:'投诉'},
                    {path:'other',name:'其他'},
                ]
            },
            {
                name:'信息管理',
                path:'info',
                children:[
                    {path:'infoshow',name:'个人信息'},
                    {path:'household',name:'同住住户'}
                ]
            },
            ]
        }
    }
}
</script>


<style scoped>
.menu_page {
  position: fixed;
  left: 0;
  min-height: 100%;
  background-color: #918081;
  z-index: 99;
}
.el-menu {
  border: none;
}
.fa-margin {
  margin-right: 5px;
}
.el-menu-vertical-demo:not(.el-menu--collapse) {
  width: 180px;
  min-height: 800px;
}
.el-menu-vertical-demo {
  width: 35px;
}
.el-sub-menu .el-menu-item {
  min-width: 180px;
}

.hiddenDropdown,
.hiddenDropname {
  display: none;
}
a {
  text-decoration: none;
}
</style>