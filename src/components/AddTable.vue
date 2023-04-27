<template>
  <div class="add-layot">
    <div class="button-add" @click="addNewRow">
      <svg
        width="11px"
        height="11px"
        viewBox="0 0 11 11"
        version="1.1"
        xmlns="http://www.w3.org/2000/svg"
        xmlns:xlink="http://www.w3.org/1999/xlink"
        class="button-add__icon"
      >
        <title>Combined Shape</title>
        <g
          id="Журнал"
          stroke="none"
          stroke-width="1"
          fill="none"
          fill-rule="evenodd"
        >
          <g
            id="Логистика-Copy-39"
            transform="translate(-289.000000, -154.000000)"
            fill="#1253a2"
          >
            <g id="Group-10" transform="translate(254.000000, 122.000000)">
              <g
                id="Кнопка-в-корзину"
                transform="translate(25.000000, 20.000000)"
              >
                <path
                  d="M15.5,12 C15.7761424,12 16,12.2238576 16,12.5 L16,17 L20.5,17 C20.7761424,17 21,17.2238576 21,17.5 C21,17.7761424 20.7761424,18 20.5,18 L16,18 L16,22.5 C16,22.7761424 15.7761424,23 15.5,23 C15.2238576,23 15,22.7761424 15,22.5 L15,17.999 L10.5,18 C10.2238576,18 10,17.7761424 10,17.5 C10,17.2238576 10.2238576,17 10.5,17 L15,16.999 L15,12.5 C15,12.2238576 15.2238576,12 15.5,12 Z"
                  id="Combined-Shape"
                ></path>
              </g>
            </g>
          </g>
        </g>
      </svg>
      <div class="button-add__title">Добавить строку</div>
    </div>
  </div>
</template>
<script>
export default {
  name: "AddTable",

  emits: {
    "add-new-row": (value) => typeof value === "string",
  },

  methods: {
    addNewRow() {
      this.$emit("add-new-row", "added");
    },
  },
};
</script>
<style lang="scss" scoped>
@import "../assets/css/colors.scss";
.add-layot {
  height: 75px;
  border-radius: 10px;
  box-shadow: 0 5px 20px 0 $black-7;
  border: solid 1px $pale-grey-two;
  background-color: $white;
  margin-bottom: 25px;
}
.button-add {
  width: 146px;
  height: 35px;
  border-radius: 5px;
  background-color: $dodger-blue;
  margin: 20px 0px 20px 25px;
  display: flex;
  align-items: center;
  padding: 10px 15px 10px 10px;
  cursor: pointer;

  &__icon {
    width: 11px;
    height: 11px;
  }

  &__title {
    margin: 0 0 0 7px;
    font-family: "Myriad Pro", sans-serif;
    font-size: 14px;
    color: $white;
  }
}
</style>
