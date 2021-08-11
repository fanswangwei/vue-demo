<template>
  <div class="organize-map">
    <div
      class="map-container"
      ref="myPage"
      @click="isShowNodeMenuPanel = false"
    >
      <SeeksRelationGraph
        ref="seeksRelationGraph"
        :options="graphOptions"
        :on-node-click="onNodeClick"
        :on-line-click="onLineClick"
      >
        <div
          class="node-item"
          :class="'node-item-' + node.data.level"
          slot="node"
          slot-scope="{ node }"
        >
          <div
            @click="showNodeMenus(node, $event)"
            @contextmenu.prevent.stop="showNodeMenus(node, $event)"
          >
            {{ node.text }}
          </div>
        </div>
        <div slot="bottomPanel">
          这里是底部插槽 slot="bottomPanel",可以自定义这里的内容
        </div>
      </SeeksRelationGraph>
    </div>
    <div
      v-show="isShowNodeMenuPanel"
      :style="{
        left: nodeMenuPanelPosition.x + 'px',
        top: nodeMenuPanelPosition.y + 'px'
      }"
    >
      <div>
        对这个节点进行操作：
      </div>
      <div class="c-node-menu-item" @click.stop="doAction('操作1')">操作1</div>
      <div class="c-node-menu-item" @click.stop="doAction('操作1')">操作2</div>
      <div class="c-node-menu-item" @click.stop="doAction('操作1')">操作3</div>
      <div class="c-node-menu-item" @click.stop="doAction('操作1')">操作4</div>
    </div>
  </div>
</template>

<script>
import SeeksRelationGraph from './src';
export default {
  name: 'Demo',
  components: { SeeksRelationGraph },
  data() {
    return {
      isShowCodePanel: false,
      isShowNodeMenuPanel: false,
      nodeMenuPanelPosition: { x: 0, y: 0 },
      graphOptions: {
        // 这里可以参考"Graph 图谱"中的参数进行设置
        debug: true,
        allowSwitchLineShape: true,
        allowSwitchJunctionPoint: true,
        defaultExpandHolderPosition: 'right',
        defaultNodeBorderWidth: 0,
        defaultNodeWidth: 50,
        defaultNodeHeight: 50,
        defaultLineColor: 'rgba(0, 186, 189, 1)',
        defaultNodeColor: 'transparent',
        layouts: [
          {
            label: '中心',
            layoutName: 'force'
          }
        ]
      }
    };
  },
  created() {
    document.title = '组织地图';
  },
  mounted() {
    this.showSeeksGraph();
    console.log(this.$refs.seeksRelationGraph.graphSetting);
  },
  methods: {
    showSeeksGraph(query) {
      var __graph_json_data = {
        rootId: 'a',
        nodes: [
          {
            id: 'a',
            text: 'a',
            data: {
              level: 1
            }
          },
          {
            id: 'b',
            text: 'b',
            data: {
              level: 2
            }
          },
          {
            id: 'b1',
            text: 'b1',
            data: {
              level: 3
            }
          },
          {
            id: 'b1-1',
            text: 'b1-1'
          },
          {
            id: 'b1-2',
            text: 'b1-2'
          },
          {
            id: 'b1-3',
            text: 'b1-3'
          },
          {
            id: 'b2',
            text: 'b2',
            data: {
              level: 3
            }
          },
          {
            id: 'b2-1',
            text: 'b2-1'
          },
          {
            id: 'b2-2',
            text: 'b2-2'
          },
          {
            id: 'b3',
            text: 'b3',
            data: {
              level: 3
            }
          },
          {
            id: 'b3-1',
            text: 'b3-1'
          },
          {
            id: 'b3-2',
            text: 'b3-2'
          },
          {
            id: 'b4',
            text: 'b4',
            data: {
              level: 3
            }
          },
          {
            id: 'b4-1',
            text: 'b4-1'
          },
          {
            id: 'b4-2',
            text: 'b4-2'
          },
          {
            id: 'b4-3',
            text: 'b4-3'
          },
          {
            id: 'b5',
            text: 'b5',
            data: {
              level: 3
            }
          },
          {
            id: 'b5-1',
            text: 'b5-1'
          },
          {
            id: 'b5-2',
            text: 'b5-2'
          },
          {
            id: 'b5-3',
            text: 'b5-3'
          },
          {
            id: 'b5-4',
            text: 'b5-4'
          },
          {
            id: 'b6',
            text: 'b6',
            data: {
              level: 3
            }
          },
          {
            id: 'b6-1',
            text: 'b6-1'
          },
          {
            id: 'b6-2',
            text: 'b6-2'
          },
          {
            id: 'b6-3',
            text: 'b6-3'
          },
          {
            id: 'b6-4',
            text: 'b6-4'
          },
          {
            id: 'b6-5',
            text: 'b6-5'
          },
          {
            id: 'c',
            text: 'c',
            data: {
              level: 2
            }
          },
          {
            id: 'c1',
            text: 'c1',
            data: {
              level: 3
            }
          },
          {
            id: 'c1-1',
            text: 'c1-1'
          },
          {
            id: 'c1-2',
            text: 'c1-2'
          },
          {
            id: 'c1-3',
            text: 'c1-3'
          },
          {
            id: 'c1-4',
            text: 'c1-4'
          },
          {
            id: 'c1-5',
            text: 'c1-5'
          },
          {
            id: 'c1-6',
            text: 'c1-6'
          },
          {
            id: 'c1-7',
            text: 'c1-7'
          },
          {
            id: 'c2',
            text: 'c2',
            data: {
              level: 3
            }
          },
          {
            id: 'c2-1',
            text: 'c2-1'
          },
          {
            id: 'c2-2',
            text: 'c2-2'
          },
          {
            id: 'c3',
            text: 'c3',
            data: {
              level: 3
            }
          },
          {
            id: 'c3-1',
            text: 'c3-1'
          },
          {
            id: 'c3-2',
            text: 'c3-2'
          },
          {
            id: 'c3-3',
            text: 'c3-3'
          },
          {
            id: 'd',
            text: 'd',
            data: {
              level: 2
            }
          },
          {
            id: 'd1',
            text: 'd1',
            data: {
              level: 3
            }
          },
          {
            id: 'd1-1',
            text: 'd1-1'
          },
          {
            id: 'd1-2',
            text: 'd1-2'
          },
          {
            id: 'd1-3',
            text: 'd1-3'
          },
          {
            id: 'd1-4',
            text: 'd1-4'
          },
          {
            id: 'd2',
            text: 'd2',
            data: {
              level: 3
            }
          },
          {
            id: 'd2-1',
            text: 'd2-1'
          },
          {
            id: 'd2-2',
            text: 'd2-2'
          },
          {
            id: 'd3',
            text: 'd3',
            data: {
              level: 3
            }
          },
          {
            id: 'd3-1',
            text: 'd3-1'
          },
          {
            id: 'd3-2',
            text: 'd3-2'
          },
          {
            id: 'd3-3',
            text: 'd3-3'
          },
          {
            id: 'd4',
            text: 'd4',
            data: {
              level: 3
            }
          },
          {
            id: 'd4-1',
            text: 'd4-1'
          },
          {
            id: 'd4-2',
            text: 'd4-2'
          },
          {
            id: 'd4-3',
            text: 'd4-3'
          },
          {
            id: 'd4-4',
            text: 'd4-4'
          },
          {
            id: 'e',
            text: 'e',
            data: {
              level: 2
            }
          },
          {
            id: 'e1',
            text: 'e1',
            data: {
              level: 3
            }
          },
          {
            id: 'e1-1',
            text: 'e1-1'
          },
          {
            id: 'e1-2',
            text: 'e1-2'
          },
          {
            id: 'e1-3',
            text: 'e1-3'
          },
          {
            id: 'e2',
            text: 'e2',
            data: {
              level: 3
            }
          },
          {
            id: 'e2-1',
            text: 'e2-1'
          },
          {
            id: 'e2-2',
            text: 'e2-2'
          },
          {
            id: 'e2-3',
            text: 'e2-3'
          }
        ],
        links: [
          {
            from: 'a',
            to: 'b'
          },
          {
            from: 'b',
            to: 'b1'
          },
          {
            from: 'b1',
            to: 'b1-1'
          },
          {
            from: 'b1',
            to: 'b1-2'
          },
          {
            from: 'b1',
            to: 'b1-3'
          },
          {
            from: 'b',
            to: 'b2'
          },
          {
            from: 'b2',
            to: 'b2-1'
          },
          {
            from: 'b2',
            to: 'b2-2'
          },
          {
            from: 'b',
            to: 'b3'
          },
          {
            from: 'b3',
            to: 'b3-1'
          },
          {
            from: 'b3',
            to: 'b3-2'
          },
          {
            from: 'b',
            to: 'b4'
          },
          {
            from: 'b4',
            to: 'b4-1'
          },
          {
            from: 'b4',
            to: 'b4-2'
          },
          {
            from: 'b4',
            to: 'b4-3'
          },
          {
            from: 'b',
            to: 'b5'
          },
          {
            from: 'b5',
            to: 'b5-1'
          },
          {
            from: 'b5',
            to: 'b5-2'
          },
          {
            from: 'b5',
            to: 'b5-3'
          },
          {
            from: 'b5',
            to: 'b5-4'
          },
          {
            from: 'b',
            to: 'b6'
          },
          {
            from: 'b6',
            to: 'b6-1'
          },
          {
            from: 'b6',
            to: 'b6-2'
          },
          {
            from: 'b6',
            to: 'b6-3'
          },
          {
            from: 'a',
            to: 'c'
          },
          {
            from: 'c',
            to: 'c1'
          },
          {
            from: 'c1',
            to: 'c1-1'
          },
          {
            from: 'c1',
            to: 'c1-2'
          },
          {
            from: 'c1',
            to: 'c1-3'
          },
          {
            from: 'c',
            to: 'c2'
          },
          {
            from: 'c2',
            to: 'c2-1'
          },
          {
            from: 'c2',
            to: 'c2-2'
          },
          {
            from: 'c',
            to: 'c3'
          },
          {
            from: 'c3',
            to: 'c3-1'
          },
          {
            from: 'c3',
            to: 'c3-2'
          },
          {
            from: 'c3',
            to: 'c3-3'
          },
          {
            from: 'a',
            to: 'd'
          },
          {
            from: 'd',
            to: 'd1'
          },
          {
            from: 'd1',
            to: 'd1-1'
          },
          {
            from: 'd1',
            to: 'd1-2'
          },
          {
            from: 'd1',
            to: 'd1-3'
          },
          {
            from: 'd',
            to: 'd2'
          },
          {
            from: 'd2',
            to: 'd2-1'
          },
          {
            from: 'd2',
            to: 'd2-2'
          },
          {
            from: 'd',
            to: 'd3'
          },
          {
            from: 'd3',
            to: 'd3-1'
          },
          {
            from: 'd3',
            to: 'd3-2'
          },
          {
            from: 'd3',
            to: 'd3-3'
          },
          {
            from: 'd',
            to: 'd4'
          },
          {
            from: 'd4',
            to: 'd4-1'
          },
          {
            from: 'd4',
            to: 'd4-2'
          },
          {
            from: 'd4',
            to: 'd4-3'
          },
          {
            from: 'a',
            to: 'e'
          },
          {
            from: 'e',
            to: 'e1'
          },
          {
            from: 'e1',
            to: 'e1-1'
          },
          {
            from: 'e1',
            to: 'e1-2'
          },
          {
            from: 'e1',
            to: 'e1-3'
          },
          {
            from: 'e',
            to: 'e2'
          },
          {
            from: 'e2',
            to: 'e2-1'
          },
          {
            from: 'e2',
            to: 'e2-2'
          },
          {
            from: 'e2',
            to: 'e2-3'
          }
        ]
      };
      // let newArr = __graph_json_data.nodes.map(item => {
      //   (item.color = '#ec6941'),
      //     (item.styleClass = 'node-item'),
      //     (item.borderColor = '#ff875e');
      //   return item;
      // });
      // console.log(newArr);
      // console.log(JSON.stringify(newArr));
      this.$refs.seeksRelationGraph.setJsonData(
        __graph_json_data,
        seeksRGGraph => {
          // 这些写上当图谱初始化完成后需要执行的代码
        }
      );
    },
    onNodeClick(nodeObject, $event) {
      console.log('onNodeClick:', nodeObject);
    },
    onLineClick(lineObject, $event) {
      console.log('onLineClick:', lineObject);
    },
    showNodeMenus(nodeObject, $event) {
      this.currentNode = nodeObject;
      var _base_position = this.$refs.myPage.getBoundingClientRect();
      console.log('showNodeMenus:', $event, _base_position);
      this.isShowNodeMenuPanel = true;
      this.nodeMenuPanelPosition.x = $event.clientX - _base_position.x;
      this.nodeMenuPanelPosition.y = $event.clientY - _base_position.y;
    },
    doAction(actionName) {
      this.$notify({
        title: '提示',
        message: '对节点【' + this.currentNode.text + '】进行了：' + actionName,
        type: 'success'
      });
      this.isShowNodeMenuPanel = false;
    }
  }
};
</script>

<style lang="scss"></style>

<style lang="scss" scoped>
.organize-map {
  width: calc(100% - 200px);
  height: calc(100vh - 100px);
  margin-top: 50px;
  margin-left: 100px;
  .map-container {
    width: 100%;
    height: 100%;
    .rel-node-peel {

    }
    /deep/.rel-node-type-node {
      display: flex;
      align-items: center;
      justify-content: center;
      &.rel-node-checked {
        box-shadow: 0px 0px 10px #009588;
      }
    }
    .node-item {
      width: 60%;
      height: 60%;
      border-radius: 50%;
      border: 1px solid #009588;
      color: #009588;
      /deep/.el-progress {
        width: 100%;
        height: 100%;
        .el-progress-circle {
          width: 100% !important;
          height: 100% !important;
        }
      }
      &.node-item-1 {
        width: 100%;
        height: 100%;
        border: 1px solid #007799;
        color: #007799;
      }
      &.node-item-2 {
        width: 85%;
        height: 85%;
        border: 1px solid #770099;
        color: #770099;
      }
      &.node-item-3 {
        width: 70%;
        height: 70%;
        border: 1px solid #779900;
        color: #779900;
      }
    }
  }
}
.c-node-menu-item {
  line-height: 30px;
  padding-left: 10px;
  cursor: pointer;
  color: #444444;
  font-size: 14px;
  border-top: #efefef solid 1px;
}
.c-node-menu-item:hover {
  background-color: rgba(66, 187, 66, 0.2);
}
</style>
