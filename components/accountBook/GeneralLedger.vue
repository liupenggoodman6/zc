<template>
    <div class="page-tab">
        
        <div class="wrapperNew">
            <div name="main-top-bar" class="mod-toolbar-top">
                <div class="left" style="display: inline-block;">
                    <span>总账</span>
                    <div class="menu-btn" style="display: inline-block;"> 
                        <el-form label-width="65px" :model="formLabelAlign" inline-message size="small" style="display:none">
                            <el-form-item label="会计期间:">
                                <el-input ></el-input>
                            </el-form-item>
                            <el-form-item label="起始科目:">
                                <el-input ></el-input>
                            </el-form-item>
                            <el-form-item label="结束科目:">
                                <el-input ></el-input><span>至</span><el-input ></el-input>
                            </el-form-item>
                            <el-form-item label="科目级次:">
                                <el-input ></el-input><span>至</span><el-input ></el-input>
                            </el-form-item>
                            <el-form-item label="币别:">
                                <el-input ></el-input>
                            </el-form-item>
                            <div>
                                <el-checkbox label="显示辅助核算"></el-checkbox>
                            </div>
                            <div>
                                <el-checkbox label="余额为0不显示"></el-checkbox>
                            </div>
                            <div>
                                <el-checkbox label="无发生额且余额为0不显示"></el-checkbox>
                            </div>
                            <div>
                                <el-checkbox label="无发生额不显示本期合计、本年累计"></el-checkbox>
                            </div>
                            <div class="btns">
                                <a href="#" id="conditions-trigger" class="conditions-trigger conditions-expand" tabindex="-1">收起更多<b></b></a>
                                <el-button class="ui-btn ui-btn-sp" id="filter-submit" href="javascript:;">重置</el-button>
                                <el-button class="ui-btn" id="filter-reset" href="#" tabindex="-1" style="display: inline;">确定</el-button>
                            </div>
                        </el-form>
                    </div>
                    <el-button type="primary" size="small" icon="el-icon-refresh"></el-button>
                </div>
                <div class="right" style="display: inline-block;">
                    <el-button type="primary" size="small">打印</el-button>
                    <el-button type="primary" size="small">导出</el-button>
                </div>
            </div>
            <el-table :data="tableData" border show-summary style="width: 100%">          
                <el-table-column prop="code" label="科目编码" width="85" align="center"></el-table-column>
                <el-table-column prop="balanceDirection" label="科目名称" width="355" align="center"></el-table-column>
                <el-table-column prop="balanceDirection" label="期间" width="105" align="center"></el-table-column>
                <el-table-column prop="auxiliaryAccounting" label="摘要" width="155" align="center"></el-table-column>
                <el-table-column prop="auxiliaryAccounting" label="借方" width="105" align="center"></el-table-column>
                <el-table-column prop="balanceDirection" label="贷方" width="105" align="center"></el-table-column>
                <el-table-column prop="auxiliaryAccounting" label="方向" width="65" align="center"></el-table-column>
                <el-table-column prop="auxiliaryAccounting" label="余额" width="105" align="center"></el-table-column>
            </el-table>
            <el-pagination background  @size-change="handleSizeChange" @current-change="handleCurrentChange" :current-page="form.currentPage" :page-sizes="[100,  300, 500]" :page-size="form.pagesize" layout="total, sizes, prev, pager, next" :total="form.total"></el-pagination>
        </div>
    </div>
</template>
<script>
export default {
    data(){
        return {
            form:{
                typeList:[],
                status:false,
                pageNum:"1",
                pagesize:10000,
                total:100,
                currentPage:1,
            }
        }
    },
    methods: {
      handleCurrentChange(){

      },
      handleSizeChange(){

      },
      handleSelectionChange(){

      },
      handleClick(){

      },
      init(){
          console.log(this.$api.setting.getSubjiectType)
          this.$financeaxios.get(this.$api.setting.getSubjiectType,{

          }).then((res)=>{
              console.log(res)
              this.typeList = res.data;
          }).catch((error)=>{
              console.log(error);
          })
      }
    },
    created(){
        this.init()
    }
}
</script>
<style>
    
    .mod-toolbar-top {
        padding: 10px 16px;
        margin: 16px 0;
        color: #2E3033;
        zoom: 1;
    }
</style>