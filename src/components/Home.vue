<template>
  <a-menu @click="navClick"
                style="width: 256px"
                v-model="currentSelectChild"
                @openChange="onOpenChange"
                :openKeys="currentParent"
                theme="dark"
                mode="inline">
            <a-sub-menu v-for="itParent in NavData" :key="itParent.NavID">
                <span slot="title">
                    <a-icon :type="itParent.Icons" />
                    <span>{{itParent.Title}}</span>
                </span>
                <a-menu-item v-for="itChild in itParent.Child" :key="itChild.NavID">
                    <router-link :to="itChild.Path"><!--根据路径去跳转页面-->
                        {{itChild.Title}}
                    </router-link>
                </a-menu-item>
            </a-sub-menu>
     </a-menu>
</template>
<script>
export default {
  name: 'home',
  data () {
    return {
      NavData: [
        {
          NavID: 100,
          Icons: 'dashboard',
          Title: '操作',
          Path: '',
          Child: [
            {
              NavID: 101,
              Icons: '',
              Title: '用户',
              Path: '/UserInfo'
            }, {
              NavID: 102,
              Icons: '',
              Title: '公司',
              Path: '/CompanyInfo'
            }, {
              NavID: 103,
              Icons: '',
              Title: '部门',
              Path: '/TeamInfo'
            }

          ]
        }, {
          NavID: 300,
          Icons: 'audit',
          Title: '报表',
          Path: '',
          Child: [{
            NavID: 301,
            Icons: '',
            Title: '打卡',
            Path: '/Card'
          }]
        }
      ]};
  }

};
</script>
