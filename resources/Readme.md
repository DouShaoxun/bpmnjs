# Activiti7整合BPMN-JS说明
### 打开/app/index.js 
### 注释以下内容
 ```
import propertiesProviderModule from 'bpmn-js-properties-panel/lib/provider/camunda';
import camundaModdleDescriptor from 'camunda-bpmn-moddle/resources/camunda.json';
 ```

### 注释以下内容
 ```
var bpmnModeler = new BpmnModeler({
  container: canvas,
  propertiesPanel: {
    parent: '#js-properties-panel'
  },
  additionalModules: [
    propertiesPanelModule,
    propertiesProviderModule
  ],
  moddleExtensions: {
    camunda: camundaModdleDescriptor
  }
});
 ```

### 添加以下内容
 ```
import propertiesProviderModule from '../resources/properties-panel/provider/activiti';
import activitiModdleDescriptor from '../resources/activiti.json';
import customTranslate from '../resources/customTranslate/customTranslate';
import customControlsModule from '../resources/customControls';

// 添加翻译组件
var customTranslateModule = {
    translate: ['value', customTranslate]
};


var bpmnModeler = new BpmnModeler({
    container: canvas,
    propertiesPanel: {
        parent: '#js-properties-panel'
    },
    additionalModules: [
        propertiesPanelModule,
        propertiesProviderModule,
        customControlsModule,
        customTranslateModule
    ],
    moddleExtensions: {
        activiti:activitiModdleDescriptor
    }
});

 ```



### 增加BPMNJS可执行选框默认勾选，打开resources/newDiagram.bpmn
### 属性修改为isExecutable="true
 ```
<bpmn2:process id="Process_1" isExecutable="true">
 ```

### 使用命令行执行命令
 ```
npm install

npm run dev
 ```
