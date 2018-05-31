<style scoped>
  .ivu-layout {
    background-color: #f9fafb;
  }
  
  .layout {
    background: #f5f7f9;
    position: relative;
    border-radius: 4px;
    overflow: hidden;
  }
  
  .layout-header-bar {
    background: #fff;
    border-bottom: 1px solid rgba(0, 0, 0, .0625);
  }
  
  .layout-logo-left {
    width: 90%;
    height: 30px;
    background: #5b6270;
    border-radius: 3px;
    margin: 15px auto;
  }
  
  .ivu-menu-vertical.ivu-menu-light:after {
    background: rgba(0, 0, 0, .0625);
  }
  
  .menu-icon {
    transition: all .3s;
  }
  
  .rotate-icon {
    transform: rotate(-90deg);
  }
  
  .menu-item span {
    display: inline-block;
    overflow: hidden;
    width: 69px;
    text-overflow: ellipsis;
    white-space: nowrap;
    vertical-align: bottom;
    transition: width .2s ease .2s;
  }
  
  .menu-item i {
    transform: translateX(0px);
    transition: font-size .2s ease, transform .2s ease;
    vertical-align: middle;
    font-size: 16px;
  }
  
  .collapsed-menu span {
    width: 0px;
    transition: width .2s ease;
  }
  
  .collapsed-menu i {
    transform: translateX(5px);
    transition: font-size .2s ease .2s, transform .2s ease .2s;
    vertical-align: middle;
    font-size: 22px;
  }
  
  .memu_title {
    display: hidden!important;
  }
  
  .logo_img {
    margin-top: 10px;
  }
  
  .logo_img1 {
    margin-top: 0px;
  }
  .use_opt_menu{
    list-style-type:none;  
  }
  .use_opt_menu li{
    float:left;
    margin-left: 20px;
  }
  .use_opt_menu .ivu-badge-count{
    width:10px;
    height: 10px;
  }

  .use_opt_menu li{
    padding-left:25px;
  }
  .use_opt_menu .ivu-dropdown-menu li{
    padding-left: 0px;
  }
  .ivu-layout-header {
    padding: 0px;
  }
</style>

<template>
  <div class="layout">
    <Layout>
      <Sider ref="side1" hide-trigger collapsible :collapsed-width="78" v-model="isCollapsed" :style="{background:'white',}">
        <div style="height:6.5vh;min-height:65px;border-bottom: 1px solid rgba(0,0,0,.0625);text-align:center;border-right:1px solid rgba(0,0,0,.0625)">
          <img :src="logo_img" alt="" :class="logo_cls">
        </div> 
        <Menu active-name="0" theme="light" width="auto" :style="{height:'93vh'}" :class="menuitemClasses">
          <MenuItem name="1">
          <Icon type="ios-navigate"></Icon>
          <label for="" :hidden="memu_title">工作台</label>
          </MenuItem>

          <Submenu name="2">
            <template slot="title">
                          <Icon type="wand"></Icon>
                          <label for="" :hidden="memu_title">单日情况</label>
</template>
                    <MenuItem name="1-1"><label for="" :hidden="memu_title">单日客户情况</label></MenuItem>
                    <MenuItem name="1-2"><label for="" :hidden="memu_title">远期房态</label></MenuItem>
                </Submenu>
                
                        <Submenu name="3">

                          <template slot="title">
                            <Icon type="social-buffer"></Icon>
                            <label for="" :hidden="memu_title">店务系统</label>
                            </template>

                            <MenuItem name="1-1"><label for="" :hidden="memu_title">收银台</label></MenuItem>
                            <MenuItem name="1-2"><label for="" :hidden="memu_title">营业记录</label></MenuItem>
                            <MenuItem name="1-1"><label for="" :hidden="memu_title">排班管理</label></MenuItem>
                        </Submenu>

                        <Submenu name="4">
                          <template slot="title">
                            <Icon type="android-contacts"></Icon>
                            <label for="" :hidden="memu_title">CRM系统</label>
                          </template>
                            <MenuItem name="1-1"><label for="" :hidden="memu_title">客户管理</label></MenuItem>
                            <MenuItem name="1-2"><label for="" :hidden="memu_title">工作回访</label></MenuItem>
                            <MenuItem name="1-1"><label for="" :hidden="memu_title">CRM设置</label></MenuItem>
                        </Submenu>

                        <MenuItem name="5">
                            <Icon type="leaf"></Icon>
                            <label for="" :hidden="memu_title">用户档案</label>
                        </MenuItem>
                        <Submenu name="6">
                           <template slot="title">
                            <Icon type="aperture"></Icon>
                            <label for="" :hidden="memu_title">业务管理</label>
                            </template>
                            <MenuItem name="1-1" :hidden="memu_title"><label for="" :hidden="memu_title">销售业务管理</label></MenuItem>
                            <MenuItem name="1-2" :hidden="memu_title"><label for="" :hidden="memu_title">护理业务管理</label></MenuItem>
                            <MenuItem name="1-1" :hidden="memu_title"><label for="" :hidden="memu_title">产康业务管理</label></MenuItem>
                        </Submenu>
                        <Submenu name="7">
                          <template slot="title">
                            <Icon type="gear-b"></Icon>
                            <label for="" :hidden="memu_title">系统设置</label>
                          </template>
                            <MenuItem name="1-1"><label for="" :hidden="memu_title">版本管理</label></MenuItem>
                            <MenuItem name="1-1"><label for="" :hidden="memu_title">系统日志</label></MenuItem>
                            <MenuItem name="1-2"><label for="" :hidden="memu_title">关于我们</label></MenuItem>
                            <MenuItem name="1-1"><label for="" :hidden="memu_title">权限管理</label></MenuItem>
                        </Submenu>
                </Menu>
            </Sider>
            <Layout>
                <Header style="padding: 0,height:'6.5vh',min-height:65px;" class="layout-header-bar">
                   <Row>
                      <Col span="3" style="float:left;"><Icon @click.native="collapsedSider" :class="rotateIcon" :style="{margin: '20px 20px 0'}" type="navicon" size="24"></Icon></Col>
                      <Col span="15">&nbsp;</Col>
                      <Col span="6" >
                        <div style="float:right;margin-right:20px;">
                          <ul class="use_opt_menu">
                            <li>
                              <Badge dot>
                                <Icon type="ios-bell-outline" size="26"></Icon>
                            </Badge>
                          </li>
                            <li>
                               <Badge dot>
                                <Icon type="social-dropbox-outline" size="26"></Icon>
                            </Badge>
                            </li>
                            <li>
                            <Dropdown>
                              <a href="javascript:void(0)">
                                <Avatar src="http://img5.duitang.com/uploads/item/201506/07/20150607110911_kY5cP.jpeg" style="width:26px;height:26px;"/>
                                  <Icon type="arrow-down-b"></Icon>
                              </a>
                              <DropdownMenu slot="list" style="width:100px;left:20px;text-align:center;">
                                  <DropdownItem>系统设置</DropdownItem>
                                  <DropdownItem>退出登录</DropdownItem>
                              </DropdownMenu>
                          </Dropdown>
                            </li>
                          </ul>
                        </div>
                      </Col>
                  </Row>
                </Header>
                <Content :style="{margin: '20px', background: '#fff', minHeight: '260px'}">
                    Content
                </Content>
            </Layout>
        </Layout>
    </div>
</template>

<script>
import 'jquery'

  export default {
    data() {
      return {
        isCollapsed: false,
        memu_title: false,
        logo_img: require('../styles/images/logo2.png'),
        logo_cls: 'logo_img'
      }
    },
    computed: {
      rotateIcon() {
        return [
          'menu-icon',
          this.isCollapsed ? 'rotate-icon' : ''
        ];
      },
      menuitemClasses() {
        return [
          'menu-item',
          this.isCollapsed ? 'collapsed-menu' : ''
        ]
      }
    },
    methods: {
      collapsedSider() {
        this.memu_title = !this.memu_title
        if (this.memu_title) {
          this.logo_img = require('../styles/images/logo3.png')
          this.logo_cls = 'logo_img1'
          $('.ivu-menu-vertical .ivu-menu-submenu-title-icon').hide()
          
        } else {
          this.logo_img = require('../styles/images/logo2.png')
          this.logo_cls = 'logo_img'
          $('.ivu-menu-vertical .ivu-menu-submenu-title-icon').show()
        }
        this.$refs.side1.toggleCollapse();
      }
    }
  }
</script>