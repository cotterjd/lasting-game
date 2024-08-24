<template>
  <div :class="currentAction.color">{{ version }}
    <div class="action">{{ currentAction.action }}!</div>
    <div class="count">{{ count }}</div>
  </div>
</template>

<script>

export default {
  components: {},
  data: () => ({
    currentAction: { action: `ready?`, color: `white` }, 
    actions: [
      { action: `action1`, color: `blue` },
      { action: `action2`, color: `orange` },
      { action: `action3`, color: `pink` },
      { action: `action4`, color: `red` },
    ],
    count: 0,
    time: 0,
  }),
  watch: {},
  methods: {
    countDown() {
      if (this.count > 0) {
        setTimeout(() => {
          this.count--;
          this.countDown();
        }, 1000)
      } else {
        this.changeAction();
      }
    },
    changeAction() {
      this.currentAction = this.actions[Math.floor(Math.random() * this.actions.length)];
      const time = Math.floor(Math.random() * 10) + 2;
      this.time = time;
      this.count = time;
      this.countDown();
    }
  },
  mounted() {
    this.changeAction();
  },
};
</script>

<style scoped>
.blue {
  background-color: blue;
  height: 100vh;
  width: 100vw;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.red {
  background-color: red;
  height: 100vh;
  width: 100vw;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.orange {
  background-color: orange;
  height: 100vh;
  width: 100vw;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.pink {
  background-color: pink;
  height: 100vh;
  width: 100vw;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.action {
  font-size: 120px;
  color: black;
  text-transform: uppercase;
}

.count {
  font-size: 400px;
  color: black;
}
</style>
