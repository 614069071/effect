<template>
  <div class="box">
    <div :style="{ width: 140 * list[0].length + 'px' }" class="list-wrapper">
      <div v-for="(a, b) in list" :key="b" :class="{ reverse: b % 2 }" :style="{ width: 140 * list[0].length + 'px' }" class="wrapper">
        <div v-for="(c, d) in a" :key="d" class="item">
          <div :class="{ right: b % 2 ? d : d < a.length - 1, top: !d && b }" class="item-inner"></div>
          <div class="item-des">
            <div>{{ c.ResultStatusDesc }}</div>
            <div>{{ c.Doctor }}</div>
            <div>{{ c.ResultDate }}</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'bow-chart',
  data() {
    return {
      colle: [
        {
          ind: '1',
          ResultStatusCode: 'A',
          ResultStatusDesc: '申请',
          ResultDate: '2022-06-1',
          ResultTime: '03:53:36',
          Doctor: '何诚',
        },
        {
          ind: '2',
          ResultStatusCode: 'I',
          ResultStatusDesc: '登记',
          ResultDate: '2022-06-2',
          ResultTime: '04:00:59',
          Doctor: '何诚',
        },
        {
          ind: '3',
          ResultStatusCode: '',
          ResultStatusDesc: '报告录入',
          ResultDate: '2022-06-3',
          ResultTime: '04:00:43',
          Doctor: '邵婧',
        },
        {
          ind: '4',
          ResultStatusCode: '',
          ResultStatusDesc: '报告审核',
          ResultDate: '2022-06-4',
          ResultTime: '04:00:43',
          Doctor: '邵婧',
        },
        {
          ind: '5',
          ResultStatusCode: '',
          ResultStatusDesc: '报告发布',
          ResultDate: '2022-06-5',
          ResultTime: '04:00:43',
          Doctor: '邵婧',
        },
        {
          ind: '1',
          ResultStatusCode: 'A',
          ResultStatusDesc: '申请',
          ResultDate: '2022-06-6',
          ResultTime: '03:54:36',
          Doctor: '何诚',
        },
        {
          ind: '2',
          ResultStatusCode: 'I',
          ResultStatusDesc: '登记',
          ResultDate: '2022-06-7',
          ResultTime: '04:01:59',
          Doctor: '何诚',
        },
        {
          ind: '3',
          ResultStatusCode: '',
          ResultStatusDesc: '报告录入',
          ResultDate: '2022-06-8',
          ResultTime: '04:01:43',
          Doctor: '邵婧',
        },
        {
          ind: '4',
          ResultStatusCode: '',
          ResultStatusDesc: '报告审核',
          ResultDate: '2022-06-9',
          ResultTime: '04:01:43',
          Doctor: '邵婧',
        },
        {
          ind: '5',
          ResultStatusCode: '',
          ResultStatusDesc: '报告发布',
          ResultDate: '2022-06-10',
          ResultTime: '04:01:43',
          Doctor: '邵婧',
        },
        {
          ind: '1',
          ResultStatusCode: 'A',
          ResultStatusDesc: '申请',
          ResultDate: '2022-06-11',
          ResultTime: '03:55:36',
          Doctor: '何诚',
        },
        {
          ind: '2',
          ResultStatusCode: 'I',
          ResultStatusDesc: '登记',
          ResultDate: '2022-06-12',
          ResultTime: '04:02:59',
          Doctor: '何诚',
        },
        {
          ind: '3',
          ResultStatusCode: '',
          ResultStatusDesc: '报告录入',
          ResultDate: '2022-06-13',
          ResultTime: '04:02:43',
          Doctor: '邵婧',
        },
        {
          ind: '4',
          ResultStatusCode: '',
          ResultStatusDesc: '报告审核',
          ResultDate: '2022-06-14',
          ResultTime: '04:02:43',
          Doctor: '邵婧',
        },
        {
          ind: '5',
          ResultStatusCode: '',
          ResultStatusDesc: '报告发布',
          ResultDate: '2022-06-15',
          ResultTime: '04:02:43',
          Doctor: '邵婧',
        },
      ],
      list: [[]],
    };
  },
  mounted() {
    const width = 140;

    const change = () => {
      const a = document.body.clientWidth;
      const b = Math.floor(a / width);
      const c = this.colle.length;
      const d = Math.ceil(c / b);
      const e = [];

      for (let i = 0; i < d; i++) {
        e.push(this.colle.slice(i * b, i * b + b));
      }

      this.list = e;
    };

    change();

    window.addEventListener('resize', change);

    const arr = Array(5);

    arr.forEach((v, i) => console.log('v => ', v, i));
  },
};
</script>

<style lang="scss">
:root {
  --size: 20px;
  --line-w: 3px;
  --line-h: 30px;
  --color: green;
}

.list-wrapper {
  margin: 0 auto;
  padding-top: 40px;
  font-size: 14px;
}

.wrapper {
  display: flex;
  position: relative;
}

.wrapper.reverse {
  flex-direction: row-reverse;
}

.item {
  display: inline-flex;
  justify-content: center;
  width: 140px;
  height: 115px;

  .item-inner {
    width: var(--size);
    height: var(--size);
    border-radius: 50%;
    border: 2px solid #fff;
    background-color: var(--color);
    position: absolute;
    bottom: 100%;

    div {
      text-align: center;
      white-space: nowrap;
    }
  }
}

.item-inner.right::after {
  content: '';
  position: absolute;
  width: 140px;
  height: var(--line-w);
  background-color: var(--color);
  top: 50%;
  left: 100%;
  transform: translateY(-50%);
  z-index: -1;
}

.item-inner.top::before {
  content: '';
  position: absolute;
  width: var(--line-w);
  height: var(--line-h);
  background-color: var(--color);
  bottom: 100%;
  left: 50%;
  transform: translateX(-50%);
  z-index: -1;
}

.item-des {
  text-align: center;
  line-height: 20px;
}
</style>
