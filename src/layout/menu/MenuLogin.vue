<template>
  <div id="menu-item">
    <a-auto-complete
      class="certain-category-search"
      dropdown-class-name="certain-category-search-dropdown"
      :dropdown-match-select-width="false"
      :dropdown-style="{ width: '200px' }"
      size="large"
      style="width: 200px"
      placeholder="input here"
      option-label-prop="value"
    >
      <template slot="dataSource">
        <a-select-opt-group v-for="group in dataSource" :key="group.title">
          <span slot="label">
            {{ group.title }}
            <a
              style="float: right"
              href="#"
              rel="noopener noreferrer"
            >more
            </a>
          </span>
          <a-select-option v-for="opt in group.children" :key="opt.title" :value="opt.title">
            {{ opt.title }}
            <span class="certain-search-item-count">{{ opt.count }} people</span>
          </a-select-option>
        </a-select-opt-group>
        <a-select-option key="all" disabled class="show-all">
          <a
            href="#"
            rel="noopener noreferrer"
          >
            View all results
          </a>
        </a-select-option>
      </template>
      <a-input>
        <a-icon slot="suffix" type="search" class="certain-category-icon" />
      </a-input>
    </a-auto-complete>
    <a-divider type="vertical" />
    <a v-if="!isLogin" href="#">登录</a>
    <a-divider v-if="!isLogin" type="vertical" />
    <a v-if="!isLogin" href="#">注册</a>
    <span v-else>
      <a-dropdown placement="bottomCenter">
        <a-badge :count="1"><a-avatar shape="square" icon="user" /></a-badge>
        <a-menu slot="overlay">
          <a-menu-item>
            <a href="#">个人主页</a>
          </a-menu-item>
          <a-menu-item>
            <a href="#">账号管理</a>
          </a-menu-item>
          <a-menu-item>
            <a href="#">退出登录</a>
          </a-menu-item>
        </a-menu>
      </a-dropdown>
      <br v-if="index === 2">
    </span>
  </div>
</template>

<script>
const dataSource = [
  {
    title: 'Libraries',
    children: [
      {
        title: 'AntDesign',
        count: 10000
      },
      {
        title: 'AntDesign UI',
        count: 10600
      }
    ]
  },
  {
    title: 'Solutions',
    children: [
      {
        title: 'AntDesign UI',
        count: 60100
      },
      {
        title: 'AntDesign',
        count: 30010
      }
    ]
  },
  {
    title: 'Articles',
    children: [
      {
        title: 'AntDesign design language',
        count: 100000
      }
    ]
  }
]
export default {
  name: 'MenuLogin',
  data() {
    return {
      dataSource,
      isLogin: true
    }
  }
}
</script>

<style>
    .certain-category-search-dropdown .ant-select-dropdown-menu-item-group-title {
        color: #666;
        font-weight: bold;
    }

    .certain-category-search-dropdown .ant-select-dropdown-menu-item-group {
        border-bottom: 1px solid #f6f6f6;
    }

    .certain-category-search-dropdown .ant-select-dropdown-menu-item {
        padding-left: 16px;
    }

    .certain-category-search-dropdown .ant-select-dropdown-menu-item.show-all {
        text-align: center;
        cursor: default;
    }

    .certain-category-search-dropdown .ant-select-dropdown-menu {
        max-height: 300px;
    }
</style>

<style scoped>
    #menu-item{
        float: right;
    }
    #menu-item span{
      margin-bottom: 5px;
    }
    .certain-category-search-wrapper
    >>> .certain-category-search.ant-select-auto-complete
    .ant-input-affix-wrapper
    .ant-input-suffix {
        right: 12px;
    }
    .certain-category-search-wrapper >>> .certain-search-item-count {
        position: absolute;
        color: #999;
        right: 16px;
    }
    .certain-category-search-wrapper
    >>> .certain-category-search.ant-select-focused
    .certain-category-icon {
        color: #108ee9;
    }
    .certain-category-search-wrapper >>> .certain-category-icon {
        color: #6e6e6e;
        transition: all 0.3s cubic-bezier(0.645, 0.045, 0.355, 1);
        font-size: 16px;
    }
</style>
