<template>
  <div class="demo full">
    <h2>基础用法</h2>
    <nut-menu>
      <nut-menu-item v-model="state.value1" :options="state.options1" />
      <nut-menu-item v-model="state.value2" @change="handleChange" :options="state.options2" />
    </nut-menu>
    <h2>自定义菜单内容</h2>
    <nut-menu>
      <nut-menu-item v-model="state.value1" :options="state.options1" />
      <nut-menu-item title="筛选" ref="item">
        <div :style="{ display: 'flex', flex: 1, 'justify-content': 'space-between', 'align-items': 'center' }">
          <div>自定义内容</div>
          <nut-button @click="onConfirm">关闭</nut-button>
        </div>
      </nut-menu-item>
    </nut-menu>
    <h2>一行两列</h2>
    <nut-menu>
      <nut-menu-item v-model="state.value3" :cols="2" :options="state.options3" />
    </nut-menu>
    <h2>自定义选中态颜色</h2>
    <nut-menu active-color="green">
      <nut-menu-item v-model="state.value1" :options="state.options1" />
      <nut-menu-item v-model="state.value2" @change="handleChange" :options="state.options2" />
    </nut-menu>
    <h2>禁用菜单</h2>
    <nut-menu>
      <nut-menu-item disabled v-model="state.value1" :options="state.options1" />
      <nut-menu-item disabled v-model="state.value2" @change="handleChange" :options="state.options2" />
    </nut-menu>
  </div>
</template>

<script lang="ts">
import { reactive, ref } from 'vue';
import { createComponent } from '../../utils/create';
const { createDemo } = createComponent('menu');
export default createDemo({
  props: {},
  setup() {
    const state = reactive({
      options1: [
        { text: '全部商品', value: 0 },
        { text: '新款商品', value: 1 },
        { text: '活动商品', value: 2 }
      ],
      options2: [
        { text: '默认排序', value: 'a' },
        { text: '好评排序', value: 'b' },
        { text: '销量排序', value: 'c' }
      ],
      options3: [
        { text: '全部商品', value: 0 },
        { text: '家庭清洁/纸品', value: 1 },
        { text: '个人护理', value: 2 },
        { text: '美妆护肤', value: 3 },
        { text: '食品饮料', value: 4 },
        { text: '家用电器', value: 5 },
        { text: '母婴', value: 6 },
        { text: '数码', value: 7 },
        { text: '电脑、办公', value: 8 },
        { text: '运动户外', value: 9 },
        { text: '厨具', value: 10 },
        { text: '医疗保健', value: 11 },
        { text: '酒类', value: 12 },
        { text: '生鲜', value: 13 },
        { text: '家具', value: 14 },
        { text: '传统滋补', value: 15 },
        { text: '汽车用品', value: 16 },
        { text: '家居日用', value: 17 }
      ],
      value1: 0,
      value2: 'a',
      value3: 0
    });

    const item = ref('');

    const onConfirm = () => {
      item.value.toggle();
    };

    const handleChange = (val) => {
      console.log('val', val);
    };

    return {
      state,
      item,
      onConfirm,
      handleChange
    };
  }
});
</script>
