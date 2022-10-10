<template>
  <div class="box">
    <div :style="{ width: 140 * row[0].length + 'px' }" class="bow-wrapper">
      <div v-for="(a, b) in row" :key="b" :class="{ reverse: b % 2 }" class="wrapper">
        <div v-for="(c, d) in a" :key="d" class="item">
          <div :class="{ right: b % 2 ? d : d < a.length - 1, top: !d && b }" class="indicator"></div>
          <div class="item-des">
            <div>{{ c.des }}</div>
            <div>{{ c.doctor }}</div>
            <div>{{ c.date }}</div>
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
          des: '申请',
          date: '2022-06-1',
          doctor: '何诚',
        },
        {
          ind: '2',
          des: '登记',
          date: '2022-06-2',
          doctor: '何诚',
        },
        {
          ind: '3',
          des: '报告录入',
          date: '2022-06-3',
          doctor: '邵婧',
        },
        {
          ind: '4',
          des: '报告审核',
          date: '2022-06-4',
          doctor: '邵婧',
        },
        {
          ind: '5',
          des: '报告发布',
          date: '2022-06-5',
          doctor: '邵婧',
        },
        {
          ind: '1',
          des: '申请',
          date: '2022-06-6',
          doctor: '何诚',
        },
        {
          ind: '2',
          des: '登记',
          date: '2022-06-7',
          doctor: '何诚',
        },
        {
          ind: '3',
          des: '报告录入',
          date: '2022-06-8',
          doctor: '邵婧',
        },
        {
          ind: '4',
          des: '报告审核',
          date: '2022-06-9',
          doctor: '邵婧',
        },
        {
          ind: '5',
          des: '报告发布',
          date: '2022-06-10',
          doctor: '邵婧',
        },
        {
          ind: '1',
          des: '申请',
          date: '2022-06-11',
          doctor: '何诚',
        },
        {
          ind: '2',
          des: '登记',
          date: '2022-06-12',
          doctor: '何诚',
        },
        {
          ind: '3',
          des: '报告录入',
          date: '2022-06-13',
          doctor: '邵婧',
        },
        {
          ind: '4',
          des: '报告审核',
          date: '2022-06-14',
          doctor: '邵婧',
        },
        {
          ind: '5',
          des: '报告发布',
          date: '2022-06-15',
          doctor: '邵婧',
        },
      ],
      row: [[]],
    };
  },
  mounted() {
    const width = 140;

    const change = () => {
      const a = document.body.clientWidth;
      const b = Math.floor(a / width);
      const c = this.colle.length;
      const d = Math.ceil(c / b);
      const e = Array(d).fill('');

      this.row = e.map((v, i) => this.colle.slice(i * b, i * b + b));
    };

    change();

    window.addEventListener('resize', change);
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

.bow-wrapper {
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

  .indicator {
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

.indicator.right::after {
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

.indicator.top::before {
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
