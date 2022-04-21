<template>
  <section v-if="hasFruits">
    <h1>Fruits</h1>
    <ul>
      <li v-for="fruit in fruits" :key="fruit">
        {{ fruit }}
      </li>
    </ul>
  </section>
  <section>
    <h1>Reverse Fruits</h1>
    <ul>
      <li v-for="fruit in reverseFruits" :key="fruit">
        {{ fruit }}
      </li>
    </ul>
  </section>
  <section>
    <button @click="add">ADD</button>
    <!-- 매번 계산을 하는것 -->
    <h1>{{ reverseMessage() }}</h1>

    <!-- 계산된 데이터를 가져오는것 : computed : 캐싱의 기능이 있어 이렇게 가능 -->
    <h1>{{ reversedMessage }}</h1>
  </section>
</template>

<script>
export default {
  data() {
    return {
      //Getter
      //Setter : 값을 지정하는 용도

      fruits: ["apple", "banana", "cherry"],
      msg: "Hello Computed",
    };
  },
  computed: {
    hasFruits() {
      return this.fruits.length > 0;
    },

    reverseFruits() {
      return this.fruits.map((fruit) => {
        return fruit.split("").reverse().join("");
      });
    },
    //Getter : 값을 얻어내는 용도
    // 읽기 전용 :  반응적으로 반응하지는 않는다
    // reversedMessage() {
    //   return this.msg.split("").reverse().join("");
    // },

    //Getter, Setter
    reversedMessage: {
      get() {
        return this.msg.split("").reverse().join("");
      },
      set(newValue) {
        this.msg = newValue;
      },
    },
  },
  methods: {
    reverseMessage() {
      return this.msg.split("").reverse().join("");
    },
    add() {
      this.reversedMessage += "!?";
      // this.msg += "!?";
    },
  },
};
</script>
