<style scoped>
    .layout{
        border: 1px solid #d7dde4;
        background: #f5f7f9;
        position: relative;
        border-radius: 4px;
        overflow: hidden;
    }
    .layout-header-bar{
        background: #fff;
        box-shadow: 0 1px 1px rgba(0,0,0,.1);
    }
    .layout-logo-left{
        width: 90%;
        height: 30px;
        background: #5b6270;
        border-radius: 3px;
        margin: 15px auto;
    }
    .menu-icon{
        transition: all .3s;
    }
    .rotate-icon{
        transform: rotate(-90deg);
    }
    .menu-item span{
        display: inline-block;
        overflow: hidden;
        width: 69px;
        text-overflow: ellipsis;
        white-space: nowrap;
        vertical-align: bottom;
        transition: width .2s ease .2s;
    }
    .menu-item i{
        transform: translateX(0px);
        transition: font-size .2s ease, transform .2s ease;
        vertical-align: middle;
        font-size: 16px;
    }
    .collapsed-menu span{
        width: 0px;
        transition: width .2s ease;
    }
    .collapsed-menu i{
        transform: translateX(5px);
        transition: font-size .2s ease .2s, transform .2s ease .2s;
        vertical-align: middle;
        font-size: 22px;
    }
    #side {
      position:fixed;
      height:100%;
    }
    .sideRight {
      margin-left: 78px;

    }
    .content {
      margin: 1px 1px;

    }
</style>
<template>
    <div class="layout">
        <Layout>
            <div @mouseover="over" @mouseout="out">
              <Sider id="side" ref="side1" hide-trigger collapsible :collapsed-width="78" v-model="isCollapsed">
                  <Menu active-name="1-2" theme="dark" width="auto" :class="menuitemClasses">
                      <MenuItem name="1-1">
                          <Icon type="ios-navigate"></Icon>
                          <span>Option 1</span>
                      </MenuItem>
                      <MenuItem name="1-2">
                          <Icon type="ios-search"></Icon>
                          <span>Option 2</span>
                      </MenuItem>
                      <MenuItem name="1-3">
                          <Icon type="ios-settings"></Icon>
                          <span>Option 3</span>
                      </MenuItem>
                  </Menu>
              </Sider>
            </div>
            <Layout class ="sideRight">
                <Header :style="{padding: 0}" class="layout-header-bar">
                    <Icon @click.native="collapsedSider" :class="rotateIcon" :style="{margin: '0 20px'}" type="md-menu" size="24"></Icon>
                </Header>
                <Content class="content" :style="{background: '#fff'}">
                    <dash-board></dash-board>
                </Content>
            </Layout>
        </Layout>
    </div>
</template>
<script>
    import DashBoard from './dashBoard'

    export default {
        data () {
            return {
                isCollapsed: true
            }
        },
        computed: {
            rotateIcon () {
                return [
                    'menu-icon',
                    this.isCollapsed ? 'rotate-icon' : ''
                ];
            },
            menuitemClasses () {
                return [
                    'menu-item',
                    this.isCollapsed ? 'collapsed-menu' : ''
                ]
            }
        },
        methods: {
            collapsedSider () {
              this.$refs.side1.toggleCollapse();
            },
            over() {
                this.isCollapsed = false
            },
            out(){
              this.isCollapsed = true
            }
            
        },
        components:{
          DashBoard
        }
    }
</script>
