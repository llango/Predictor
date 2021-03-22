<template>
  <div class="d-flex flex-column justify-content-center align-items-center">
    <div class="p-2" style="text-align:center; margin-top:15px;">
      <h1>心脏病预测器</h1>
      <h1 v-if="APIResult.length != []" style="font-size:3.2rem; color:#ff2121;">得病情况: {{ APIResult }}</h1>  
      <h6>存在 (值 1,2,3,4) | 没有 (值为 0)</h6>
    </div>
    <div class="p-2">
        <form @submit.prevent>
            <div class="form-row" style="max-width:1024px">
                <div class="form-group col-md-3">
                    <label class="col-12 px-0" for="A">年龄</label>
                    <input
                    class="form-control"
                    v-model.trim="heartdata.A"
                    type="number"
                    id="A"
                    />
                </div>
                <div class="form-group col-md-3">
                    <label class="col-12 px-0" for="B">性别</label>
                    <input
                    class="form-control"
                    v-model.trim="heartdata.B"
                    type="number"
                    id="B"
                    />
                </div>
                <div class="form-group col-md-3">
                    <label class="col-12 px-0" for="C">胸痛类型</label>
                    <input
                    class="form-control"
                    v-model.trim="heartdata.C"
                    type="number"
                    id="C"
                    />
                </div>
                <div class="form-group col-md-3">
                    <label class="col-12 px-0" for="D">静息血压</label>
                    <input
                    class="form-control"
                    v-model.trim="heartdata.D"
                    type="number"
                    id="D"
                    />
                </div>
                <div class="form-group col-md-3">
                    <label class="col-12 px-0" for="E">胆固醇测量值</label>
                    <input
                    class="form-control"
                    v-model.trim="heartdata.E"
                    type="number"
                    id="E"
                    />
                </div>
                <div class="form-group col-md-3">
                    <label class="col-12 px-0" for="F">空腹血糖</label>
                    <input
                    class="form-control"
                    v-model.trim="heartdata.F"
                    type="number"
                    id="F"
                    />
                </div>
                <div class="form-group col-md-3">
                    <label class="col-12 px-0" for="G">静息心电图测量</label>
                    <input
                    class="form-control"
                    v-model.trim="heartdata.G"
                    type="number"
                    id="G"
                    />
                </div>
                <div class="form-group col-md-3">
                    <label class="col-12 px-0" for="H">最大心率</label>
                    <input
                    class="form-control"
                    v-model.trim="heartdata.H"
                    type="number"
                    id="H"
                    />
                </div>
                <div class="form-group col-md-3">
                    <label class="col-12 px-0" for="I">运动引起的心绞痛</label>
                    <input
                    class="form-control"
                    v-model.trim="heartdata.I"
                    type="number"
                    id="I"
                    />
                </div>
                <div class="form-group col-md-3">
                    <label class="col-12 px-0" for="J">ST抑制</label>
                    <input
                    class="form-control"
                    v-model.trim="heartdata.J"
                    type="number"
                    id="J"
                    />
                </div>
                <div class="form-group col-md-3">
                    <label class="col-12 px-0" for="K">最高运动ST段的斜率</label>
                    <input
                    class="form-control"
                    v-model.trim="heartdata.K"
                    type="number"
                    id="K"
                    />
                </div>
                <div class="form-group col-md-3">
                    <label class="col-12 px-0" for="L"> 萤光显色的主要血管数目</label>
                    <input
                    class="form-control"
                    v-model.trim="heartdata.L"
                    type="number"
                    id="L"
                    />
                </div>
                <div class="form-group col-md-3">
                    <label class="col-12 px-0" for="M">thal</label>
                    <input
                    class="form-control"
                    v-model.trim="heartdata.M"
                    type="number"
                    id="M"
                    />
                </div>
                
            <button @click="predict" type="button" class="btn btn-primary btn-lg btn-block">提交</button>
            </div>
        </form>

        
    </div>
    <div class="p-2" style="margin-bottom:60px;">
    <ul style="color:#999;">
        <li>年龄: 输入实际年龄</li>

        <li>性别: 1 = 男性, 0 = 女性</li>

        <li>胸痛类型: 值1：典型心绞痛，值2：非典型性心绞痛，值3：非心绞痛，值4：无症状</li>

        <li>静息血压: 入院时的毫米汞柱 （正常人收缩压在90mmHg、舒张压在60mmHg以上,收缩压在140mmHg、舒张压在90mmHg以下）</li>

        <li>胆固醇测量值，正常的总胆固醇不能超过5.69mmhg</li>

        <li>空腹血糖（> 120 mg/dl，1=真；0=假）</li>

        <li>静息心电图测量（0=正常，1=患有ST-T波异常，2=根据Estes的标准显示可能或确定的左心室肥大）</li>

        <li>最大心率</li>

        <li>运动引起的心绞痛（1=有过；0=没有）</li>

        <li>ST抑制，由运动引起的相对于休息引起的（“ ST”与ECG图上的位置有关。这块比较专业，可以点这个看一个解读）</li>

        <li>最高运动ST段的斜率（值1:上坡，值2:平坦，值3:下坡）</li>

        <li>萤光显色的主要血管数目（0-4）</li>

        <li>thal: 一种称为地中海贫血的血液疾病（3=正常；6=固定缺陷；7=可逆缺陷）</li>

        <li>得病情况: 心脏病（0=否，1=是）</li>
    </ul>
    </div>
  </div>
</template>

<script>
import { getAPI } from "@/axios";
export default {
    name: "Posts",
    data() {
        return {
            heartdata: {
                A: "26",
                B: "1",
                C: "1",
                D: "60",
                E: "5.69",
                F: "150",
                G: "0",
                H: "90",
                I: "1",
                J: "1",
                K: "3",
                L: "3",
                M: "7"
            },
            APIResult: [],
        };
    },
    methods: {
        // 前后端请求的地方，进行get请求，参数直接放在url后面，提交参数到后端接口。 后端接口在一般在views.py 中提供。
        predict(){
            getAPI
            .get("/posts", {
                params: {
                    A: this.heartdata.A,
                    B: this.heartdata.B,
                    C: this.heartdata.C,
                    D: this.heartdata.D,
                    E: this.heartdata.E,
                    F: this.heartdata.F,
                    G: this.heartdata.G,
                    H: this.heartdata.H,
                    I: this.heartdata.I,
                    J: this.heartdata.J,
                    K: this.heartdata.K,
                    L: this.heartdata.L,
                    M: this.heartdata.M
                }
            })
            .then(response => {
                console.log("返回数据成功！");
                this.APIResult = response.data;
                console.log(response.data);
            })
            .catch(err => {
                console.log(err);
            });
        }
    }
 };
</script>