<template>
    <v-card>
        <!-- <div class='elevation-3'>5-5</div> -->
        <v-card>
            <v-card-text>
                <p class="text-xs-right headline">{{value}}</p>
            </v-card-text>
        </v-card>
        <div class='container'>
            <v-btn
            class="item"
            v-for="key in keys"
            :key="key"
            :v-text="key"
            :color="getColor(key)"
            @click="doOp(key)"
            >
                {{key}}
            </v-btn>
        </div>
    </v-card>
</template>

<script>
const DIVIDE = "/";
const ADD = "+";
const SUBTRACT = "-";
const MULTIPLY = "X";
const EQUAL = "=";
const CLEAR = "C";
const DECIMAL = ".";
const NEGATE = "+/-";

const doMath = (val1, val2, op) => {
  switch (op) {
    case ADD:
      return val1 + val2;
    case SUBTRACT:
      return val1 - val2;
    case MULTIPLY:
      return val1 * val2;
    case DIVIDE:
      return val1 / val2;
    default:
      return 0;
  }
};
export default {
  name: "Calculator",
  data() {
    return {
      val1: 0,
      val2: 0,
      activeKey: "",
      keys: [
        7,
        8,
        9,
        ADD,
        4,
        5,
        6,
        DIVIDE,
        1,
        2,
        3,
        MULTIPLY,
        0,
        DECIMAL,
        CLEAR,
        SUBTRACT,
        NEGATE,
        EQUAL
      ]
    };
  },
  computed: {
    value() {
      if (this.activeKey === "") {
        return this.val1;
      }
      return this.val2;
    }
  },
  props: {
    msg: String
  },
  methods: {
    doOp(key) {
      if (isNaN(key)) {
        switch (key) {
          case ADD:
          case SUBTRACT:
          case MULTIPLY:
          case DIVIDE:
            this.activeKey = key;
            break;
          case EQUAL:
            this.val1 = doMath(this.val1, this.val2, this.activeKey);
            this.activeKey = "";
            this.val2 = 0;
            break;
          case CLEAR:
            this.val1 = 0;
            this.val2 = 0;
            this.activeKey = "";
            break;
        }
      } else {
        if (this.activeKey === "") {
          this.val1 = this.val1 * 10 + key;
        } else {
          this.val2 = this.val2 * 10 + key;
        }
      }
    },
    getColor(key) {
      if (!isNaN(key)) {
        return "";
      }
      if (this.activeKey === key) {
        return "accent";
      }
      return "primary";
    }
  }
};
</script>

<style scoped>
.container {
  display: grid;
  grid-template-rows: 25% 25% 25% 25%;
  grid-template-columns: 25% 25% 25% 25%;
  grid-gap: 0em;
}

.item {
  display: grid;
  justify-content: center;
}
</style>
