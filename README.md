# element-table-yiduiduo
element-table一对多布局方式
<el-table :data="tableData" :span-method="objectSpanMethod" border style="width: 100%; margin-top: 20px; text-align='center';">
                        <el-table-column label="颜色" prop="color" v-if="pro.color.length" width="180"></el-table-column>
                        <el-table-column label="尺码" prop="size" v-if="pro.size.length"></el-table-column>
                        <el-table-column label="可售数量" prop="stock">
                          <template slot-scope="scope">
                            <el-input style="width:200px;" v-model="scope.row.stock"></el-input>
                          </template>
                        </el-table-column>
                        <el-table-column label="价格(US $)" prop="price">
                          <template slot-scope="scope">
                            <el-input style="width:200px;" v-model="scope.row.price"></el-input>
                          </template>
                        </el-table-column>
                      </el-table>
                      
objectSpanMethod({ row, column, rowIndex, columnIndex }) {
      if (row.color && row.size) {
        if (columnIndex === 0) {
          if (rowIndex % this.pro.size.length === 0) {
            return {
              rowspan: this.pro.size.length,
              colspan: 1
            };
          } else {
            return {
              rowspan: 0,
              colspan: 0
            };
          }
        }
      }
    },
