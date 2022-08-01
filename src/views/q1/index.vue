<template>
  <div class="container">
    <div class="input">
      <el-card class="box-card">
        <template #header>
          <div class="card-header">
            <span>问题输入</span>
          </div>
        </template>
        <el-form :model="form" label-width="120px">
          <el-row>
            <el-col :span="4">
              <el-form-item>
                <div class="grid-content bg-purple">区域一</div>
              </el-form-item>
            </el-col>

            <el-col :span="6">
              <el-form-item label="区域形状">
                <el-select
                  v-model="form.shape1"
                  class="el-selector"
                  placeholder="请选择"
                >
                  <el-option
                    v-for="item in area_options"
                    :key="item.value"
                    :label="item.label"
                    :value="item.value"
                  />
                </el-select>
              </el-form-item>
            </el-col>

            <el-col :span="6">
              <el-form-item label="形状参数">
                <el-input v-model="form.para1" />
              </el-form-item>
            </el-col>

            <el-col :span="6">
              <el-form-item label="所需物资包数">
                <el-input v-model="form.p1_req1" />
              </el-form-item>
            </el-col>
          </el-row>

          <el-row>
            <el-col :span="4">
              <el-form-item>
                <div class="grid-content bg-purple">区域二</div>
              </el-form-item>
            </el-col>

            <el-col :span="6">
              <el-form-item label="区域形状">
                <el-select
                  v-model="form.shape2"
                  class="el-selector"
                  placeholder="请选择"
                >
                  <el-option
                    v-for="item in area_options"
                    :key="item.value"
                    :label="item.label"
                    :value="item.value"
                  />
                </el-select>
              </el-form-item>
            </el-col>

            <el-col :span="6">
              <el-form-item label="形状参数">
                <el-input v-model="form.para2" />
              </el-form-item>
            </el-col>

            <el-col :span="6">
              <el-form-item label="所需物资包数">
                <el-input v-model="form.p1_req2" />
              </el-form-item>
            </el-col>
          </el-row>

          <el-row>
            <el-col :span="4">
              <el-form-item>
                <div class="grid-content bg-purple">区域三</div>
              </el-form-item>
            </el-col>

            <el-col :span="6">
              <el-form-item label="区域形状">
                <el-select
                  v-model="form.shape3"
                  class="el-selector"
                  placeholder="请选择"
                >
                  <el-option
                    v-for="item in area_options"
                    :key="item.value"
                    :label="item.label"
                    :value="item.value"
                  />
                </el-select>
              </el-form-item>
            </el-col>

            <el-col :span="6">
              <el-form-item label="形状参数">
                <el-input v-model="form.para3" />
              </el-form-item>
            </el-col>

            <el-col :span="6">
              <el-form-item label="所需物资包数">
                <el-input v-model="form.p1_req3" />
              </el-form-item>
            </el-col>
          </el-row>

          <el-row>
            <el-col :span="4">
              <el-form-item>
                <div class="grid-content bg-purple">物资包参数</div>
              </el-form-item>
            </el-col>

            <el-col :span="6">
              <el-form-item label="误差">
                <el-input v-model="form.p1_err" />
              </el-form-item>
            </el-col>

            <el-col :span="6">
              <el-form-item label="最小置信度">
                <el-input v-model="form.minC" />
              </el-form-item>
            </el-col>
          </el-row>

          <el-row>
            <el-col :span="4">
              <el-form-item>
                <div class="grid-content bg-purple">模型优化</div>
              </el-form-item>
            </el-col>

            <el-col :span="6">
              <el-form-item label="优化等级">
                <el-select v-model="form.level" class="el-selector" placeholder="请选择">
                  <el-option
                    v-for="item in options"
                    :key="item.value"
                    :label="item.label"
                    :value="item.value"
                  />
                </el-select>
              </el-form-item>
            </el-col>
          </el-row>

          <el-form-item>
            <el-button type="primary" plain @click="onSubmit">提交</el-button>
            <el-button type="success" plain @click="model_eval(x)">模型评估</el-button>
          </el-form-item>
        </el-form>
      </el-card>
    </div>
    <div class="output">
      <el-card class="box-card">
        <template #header>
          <div class="card-header">
            <span>计算结果</span>
          </div>
        </template>
        <el-form :model="form_output" label-width="120px">
          <el-row>
            <el-col :span="4">
              <el-form-item>
                <div class="grid-content bg-purple">区域一</div>
              </el-form-item>
            </el-col>

            <el-col :span="6">
              <el-form-item label="投送数量">
                <el-input v-model="form_output.o1" />
              </el-form-item>
            </el-col>

            <el-col :span="6">
              <el-form-item label="投掷点坐标">
                <el-input v-model="form_output.loc1" />
              </el-form-item>
            </el-col>
          </el-row>
          <el-row>
            <el-col :span="4">
              <el-form-item>
                <div class="grid-content bg-purple">区域二</div>
              </el-form-item>
            </el-col>

            <el-col :span="6">
              <el-form-item label="投送数量">
                <el-input v-model="form_output.o2" />
              </el-form-item>
            </el-col>

            <el-col :span="6">
              <el-form-item label="投掷点坐标">
                <el-input v-model="form_output.loc2" />
              </el-form-item>
            </el-col>
          </el-row>

          <el-row>
            <el-col :span="4">
              <el-form-item>
                <div class="grid-content bg-purple">区域三</div>
              </el-form-item>
            </el-col>

            <el-col :span="6">
              <el-form-item label="投送数量">
                <el-input v-model="form_output.o3" />
              </el-form-item>
            </el-col>

            <el-col :span="6">
              <el-form-item label="投掷点坐标">
                <el-input v-model="form_output.loc3" />
              </el-form-item>
            </el-col>
          </el-row>

          <el-row>
            <el-col :span="4">
              <el-form-item>
                <div class="grid-content bg-purple">模型评估</div>
              </el-form-item>
            </el-col>

            <el-col :span="6">
              <el-form-item label="单次评估">
                <el-input v-model="form_output.eval1_1" />
              </el-form-item>
            </el-col>

            <el-col :span="6">
              <el-form-item label="累次评估">
                <el-input v-model="form_output.eval1_2" />
              </el-form-item>
            </el-col>
          </el-row>
        </el-form>
      </el-card>
    </div>
    <div class="picture">
      <el-card class="box-card">
        <template #header>
          <div class="card-header">
            <span>结果展示</span>
          </div>
        </template>
        <div id="mychart" class="chart" />
      </el-card>
    </div>
  </div>
</template>

<script>
import * as echarts from 'echarts'

export default {
  name: 'Q1',
  data() {
    return {
      form: {
        shape1: '1',
        para1: '[[6, 347], 50]',
        p1_req1: '2',
        shape2: '',
        para2: '',
        p1_req2: '',
        shape3: '',
        para3: '',
        p1_req3: '',
        p1_err: '',
        minC: '',
        level: '3'
      },

      form_output: {
        o1: '',
        loc1: '',
        o2: '',
        loc2: '',
        o3: '',
        loc3: '',
        eval1: '',
        eval2: ''
      },
      formLabelAlign: {
        name: '',
        region: '',
        type: ''
      },
      area_options: [
        {
          value: '0',
          label: '无'
        },
        {
          value: '1',
          label: '圆形'
        },
        {
          value: '2',
          label: '矩形'
        },
        {
          value: '3',
          label: '多边形'
        }
      ],
      options: [
        {
          value: '1',
          label: '1级'
        },
        {
          value: '2',
          label: '2级'
        },
        {
          value: '3',
          label: '3级'
        },
        {
          value: '4',
          label: '4级'
        },
        {
          value: '5',
          label: '5级'
        }
      ],
      err: '3'
    }
  },
  mounted() {
    this.chartInit()
  },

  methods: {
    chartInit() {
      // 基于刚刚准备好的 DOM 容器，初始化 EChart 实例
      var myChart = echarts.init(document.getElementById('mychart'))
      // 绘制图表
      myChart.setOption({
        title: { text: '' },
        tooltip: {},

        graphic: [
          {
            type: 'group',
            children: [
              {
                type: 'rect',
                id: 'shape1',
                shape: {
                  x: 100,
                  y: 100,
                  width: 100,
                  height: 30
                }
              },
              {
                type: 'rect',
                shape: {
                  x: 300,
                  y: 200,
                  width: 100,
                  height: 200
                }
              },
              {
                type: 'circle',
                shape: {
                  cx: 1300,
                  cy: 100,
                  r: 100
                },
                style: {
                  fill: '#faf',
                  stroke: '#999',
                  lineWidth: 2,
                  shadowBlur: 8,
                  shadowOffsetX: 3,
                  shadowOffsetY: 3,
                  shadowColor: 'rgba(0,0,0,0.3)'
                }
              }
            ]
          }
        ]
      })
    },
    onSubmit() {
      this.$message('onsubmit')
      this.form_output.o1 = 10
    }
  }
}
</script>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  flex-direction: column;
  padding: 2%;
}

.input,
.output,
.picture {
  margin: 1%;
}
.el-selector {
  width: 100%;
}

.card-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.grid-content {
  font-size: 16px;
}

.chart {
  height: 600px;
  width: 100%;
}
</style>
