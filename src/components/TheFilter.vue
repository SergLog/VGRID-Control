<template>

 <div role="tablist" class="thefilter">
    <b-card no-body class="mb-1 small" v-for="item in items" :key="item.id">
      <b-card-header header-tag="header" class="p-1" role="tab">
        <b-btn block href="#" v-b-toggle="item.collapseId" variant="primary" size="sm">{{ item.collapseName }}</b-btn>
      </b-card-header> 
      <b-collapse :id="item.collapseId" visible role="tabpanel"> 
        <!-- accordion="my-accordion" removed to let b-card opened when clicking another one -->
        <b-card-body class="p-0">
          <b-table :fields="fields" :items="item.params" thead-class="hide_header">
            <template slot="inp" slot-scope="data">
              <div :is="item.params[data.index].controll" :value="item.params[data.index].val"></div>
              <!-- item.params[data.index].controll - you can add any controll using slot, set the type of contoll in itmes array  - -->
            </template>
            <template slot="combobox" slot-scope="data">
              <b-select v-model="item.params[data.index].selected" :options="combobox_items" class="form-control-sm"></b-select>              
               {{ item.params[data.index].selected }} 
            </template>           
          </b-table>
        </b-card-body>
      </b-collapse>
    </b-card>

    <b-select v-model="selectedvalue" :options="iskl"></b-select>
 <div> {{ selectedvalue }} </div>
<div>
 </div>


  </div>
</template>

<script>

import BaseBtn from './BaseBtn.vue'
import BaseInp from './BaseInp.vue'

export default {
  components: { BaseBtn, BaseInp },
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data () {
    return {
      selectedvalue: 0,
      items:
        [{"collapseId": "1",
        "collapseName": "Объект учета",        
        "params": [
          { "selected": '%', "dbfield": "RNO_NUM", "name": "Реестровый номер", "controll": "b-select", "val": "Введите значение" },
          { "selected": '%', "dbfield": "ISKL", "name": "Исключен", "controll": "BaseInp", "val": "ssf" },
          { "selected": '%', "dbfield": "TTT", "name": "Свободен", "controll": "BaseInp", "val": "sf" },
          { "selected": '%', "dbfield": "RNO_LOA_ID", "name": "Тип", "controll": "BaseInp", "val": "ssf" }]
        },
        {"collapseId": "2",
        "collapseName": "Свидетельство",
        "params": [
          { "selected": '', "dbfield": "RNO_NUM", "name": "Реестровый номер", "controll": "BaseInp", "val": "" },
          { "selected": '', "dbfield": "ISKL", "name": "Исключен", "controll": "BaseInp", "val": "" },
          { "selected": '', "dbfield": "TTT", "name": "Свободен", "controll": "BaseInp", "val": "" },
          { "selected": '', "dbfield": "RNO_LOA_ID", "name": "Тип", "controll": "BaseInp", "val": "" }]
        }],
      combobox_items: [
        { value: "%", text: 'Содержит' },
        { value: "=", text: 'Равно' },
        { value: ">", text: 'Больше' },
        { value: "<", text: 'Меньше' }
      ],
      iskl: [
        {value: 1, text: 'Исключен'},
        {value: 2, text: 'Не исключен'}
      ],
          fields: [
         { key: 'name', label: 'name',  },
         { key: 'combobox', label: 'combobox' },
         { key: 'inp', label: 'inp' }
        //  { key: 'btn', label: 'btn' }
       ]
    }
  }
}
</script>


<style scoped>
.thefilter {  
  width: 500px;
}
.ttt{
  float: right;
}
</style>

