<template>
  <div class="board-container">
    <slot> </slot>
    <div class="board">
      <GridItem
        :selected="isSelected(item.id)"
        @click="setSelectedCell"
        v-for="(item, index) in grid"
        :key="index"
        :item="item"
      />
    </div>
  </div>
</template>

<script>
import GridItem from "./GridItem.vue";

const isEven = (num) => num % 2 === 0;
export default {
  name: "Board",
  components: {
    GridItem,
  },
  mounted(){
      document.addEventListener('keydown', this.handleKeyDown);
  },
  data() {
    return {
      selectedCell: { type: "", id: -1 },
      lastCell: { type: "", id: -1 },
      clickCount: 0,
      grid: [
        {
          id: 1,
          type: "",
        },
        {
          id: 2,
          type: "",
        },
        {
          id: 3,
          type: "",
        },
        {
          id: 4,
          type: "",
        },
        {
          id: 5,
          type: "",
        },
        {
          id: 6,
          type: "",
        },
        {
          id: 7,
          type: "",
        },
        {
          id: 8,
          type: "",
        },
        {
          id: 9,
          type: "",
        },
      ],
    };
  },
  computed: {},
  methods: {
      handleKeyDown(e) {
        if (e.keyCode == 90 && e.ctrlKey) this.undo();
      },
    isSelected(id) {
      return this.grid[id-1].type !== ''
    },
    undo(){
        this.grid[this.selectedCell.id - 1].type = this.lastCell.type;
        this.selectedCell = this.lastCell;
        this.clickCount--;
    },
    resetGame() {
      this.grid.forEach((item) => {
        item.type = "";
      });
      this.lastCell = this.selectedCell;
      this.selectedCell = { type: "", id: -1 };
      this.clickCount = 0;
    },
    setSelectedCell(e) {
      if (this.clickCount === 9) {
        this.resetGame();
        return;
      }
      if (this.grid[e.id - 1].type === "") {
        this.selectedCell = e;
        this.grid[e.id - 1].type = isEven(this.clickCount) ? "X" : "0";
        this.clickCount++;
      }
    },
  },
};
</script>

<style>
.board {
  background-color: "brown";
  max-width: 50vw;
  display: grid;
  margin-top: 50px;
  grid-template: repeat(3, 1fr) / repeat(3, 1fr);
}
</style>