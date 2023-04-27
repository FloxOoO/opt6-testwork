<template>
  <div class="table-layot">
    <div class="save" @click="saveTable(tableData)">Сохранить изменения</div>
    <settings-menu :popupData="menuData" />
    <div class="table">
      <div class="table__titles" v-for="title in tableTitles" :key="title">
        {{ title }}
      </div>
    </div>
    <draggable :list="tableData" ghost-class="ghost" class="fulltable">
      <transition-group type="transition" name="flip-list">
        <div
          v-for="row in tableData"
          :key="row.id"
          class="table"
          @dragover="isOpen = false"
        >
          <div class="table__elem-id">
            {{ row.id }}
          </div>
          <div class="table__elem-to4ki">
            <svg
              width="3px"
              height="13px"
              viewBox="0 0 3 13"
              version="1.1"
              xmlns="http://www.w3.org/2000/svg"
              xmlns:xlink="http://www.w3.org/1999/xlink"
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
                  transform="translate(-314.000000, -316.000000)"
                  fill="#A6B7D4"
                >
                  <g
                    id="Group-2-Copy-7"
                    transform="translate(254.000000, 222.000000)"
                  >
                    <g
                      id="Group-Copy-3"
                      transform="translate(1.000000, 78.000000)"
                    >
                      <g
                        id="Group-12-Copy"
                        transform="translate(59.000000, 16.000000)"
                      >
                        <path
                          d="M1.5,0 C2.32842712,-1.52179594e-16 3,0.671572875 3,1.5 C3,2.32842712 2.32842712,3 1.5,3 C0.671572875,3 1.01453063e-16,2.32842712 0,1.5 C-1.01453063e-16,0.671572875 0.671572875,1.52179594e-16 1.5,0 Z M1.5,5 C2.32842712,5 3,5.67157288 3,6.5 C3,7.32842712 2.32842712,8 1.5,8 C0.671572875,8 1.01453063e-16,7.32842712 0,6.5 C-1.01453063e-16,5.67157288 0.671572875,5 1.5,5 Z M1.5,10 C2.32842712,10 3,10.6715729 3,11.5 C3,12.3284271 2.32842712,13 1.5,13 C0.671572875,13 1.01453063e-16,12.3284271 0,11.5 C-1.01453063e-16,10.6715729 0.671572875,10 1.5,10 Z"
                          id="Combined-Shape"
                        ></path>
                      </g>
                    </g>
                  </g>
                </g>
              </g>
            </svg>
          </div>
          <div class="table__elem">
            <input
              class="table__elem-inner"
              v-model="row.name"
              @focus="openTableBlockPopup(row.id)"
            />
            <div class="table__elem-path">
              <svg
                width="3px"
                height="6px"
                viewBox="0 0 3 6"
                version="1.1"
                xmlns="http://www.w3.org/2000/svg"
                xmlns:xlink="http://www.w3.org/1999/xlink"
              >
                <title>Path 4</title>
                <g
                  id="Журнал"
                  stroke="none"
                  stroke-width="1"
                  fill="none"
                  fill-rule="evenodd"
                >
                  <g
                    id="Логистика-Copy-37"
                    transform="translate(-1530.000000, -320.000000)"
                    fill="#C0C0C0"
                  >
                    <g
                      id="Group-2-Copy-7"
                      transform="translate(254.000000, 222.000000)"
                    >
                      <g
                        id="Group-Copy-3"
                        transform="translate(1.000000, 78.000000)"
                      >
                        <g
                          id="Group-Copy-4"
                          transform="translate(1141.000000, 5.000000)"
                        >
                          <g
                            id="Group-2"
                            transform="translate(125.000000, 1.000000)"
                          >
                            <polygon
                              id="Path-4"
                              transform="translate(10.500000, 17.000000) rotate(-90.000000) translate(-10.500000, -17.000000) "
                              points="8 15.5 10.5 18.5 13 15.5"
                            ></polygon>
                          </g>
                        </g>
                      </g>
                    </g>
                  </g>
                </g>
              </svg>
            </div>
            <table-block-popup
              v-if="isOpen === row.id"
              ref="tableBlockPopup"
              @choosed-product="chooseProduct"
            />
          </div>
          <div class="table__elem">
            <input class="table__elem-inner" v-model="row.price" />
          </div>
          <div class="table__elem">
            <input class="table__elem-inner" v-model="row.amount" />
          </div>
          <div class="table__elem">
            <div class="table__elem-inner">
              {{ row.type }}
            </div>
            <div class="table__elem-path">
              <svg
                width="3px"
                height="6px"
                viewBox="0 0 3 6"
                version="1.1"
                xmlns="http://www.w3.org/2000/svg"
                xmlns:xlink="http://www.w3.org/1999/xlink"
              >
                <title>Path 4</title>
                <g
                  id="Журнал"
                  stroke="none"
                  stroke-width="1"
                  fill="none"
                  fill-rule="evenodd"
                >
                  <g
                    id="Логистика-Copy-37"
                    transform="translate(-1530.000000, -320.000000)"
                    fill="#C0C0C0"
                  >
                    <g
                      id="Group-2-Copy-7"
                      transform="translate(254.000000, 222.000000)"
                    >
                      <g
                        id="Group-Copy-3"
                        transform="translate(1.000000, 78.000000)"
                      >
                        <g
                          id="Group-Copy-4"
                          transform="translate(1141.000000, 5.000000)"
                        >
                          <g
                            id="Group-2"
                            transform="translate(125.000000, 1.000000)"
                          >
                            <polygon
                              id="Path-4"
                              transform="translate(10.500000, 17.000000) rotate(-90.000000) translate(-10.500000, -17.000000) "
                              points="8 15.5 10.5 18.5 13 15.5"
                            ></polygon>
                          </g>
                        </g>
                      </g>
                    </g>
                  </g>
                </g>
              </svg>
            </div>
          </div>
          <div class="table__elem">
            <div class="table__elem-inner">
              {{ +row.price && +row.amount ? row.price * row.amount : "-" }}
            </div>
          </div>
        </div>
      </transition-group>
    </draggable>
    <table-block-bottom :total-amount="tableDataTotal" />
  </div>
</template>
<script>
import { addItemLS, downloadFromLS } from "../stores/localStorage.js";
import { VueDraggableNext } from "vue-draggable-next";
import SettingsMenu from "./SettingsMenu.vue";
import TableBlockBottom from "./TableBlockBottom.vue";
import TableBlockPopup from "./TableBlockPopup.vue";
export default {
  name: "TableBlock",

  components: {
    draggable: VueDraggableNext,
    SettingsMenu,
    TableBlockBottom,
    TableBlockPopup,
  },

  props: {
    addProduct: {
      type: Boolean,
      required: false,
    },
  },

  created() {
    if (downloadFromLS("table")) {
      this.tableData = downloadFromLS("table");
    }
  },

  data() {
    return {
      tableData: [
        {
          id: 1,
          name: "Мраморный щебень фр. 2-5 мм, 25кг",
          price: 1231,
          amount: 12,
          type: "Мраморный щебень фр. 2-5 мм",
        },
        {
          id: 2,
          name: "Мраморный щебень фр. 2-5 мм, 25кг",
          price: 1231,
          amount: 12,
          type: "Мраморный щебень фр. 2-5 мм",
        },
        {
          id: 3,
          name: "Мраморный щебень фр. 2-5 мм, 25кг",
          price: 1231,
          amount: 12,
          type: "Мраморный щебень фр. 2-5 мм",
        },
      ],
      selectedID: null,
      tableDataTotal: {
        fullprice: 44316,
        fullamount: 36,
        weight: 900,
      },
      isOpen: null,
    };
  },

  methods: {
    chooseProduct(product) {
      this.tableData.forEach((row, i) => {
        if (row.id === this.selectedID) {
          this.tableData[i].name = product;
          this.tableData[i].type = product.split(",")[0];
        }
      });
      this.isOpen = null;
    },
    openTableBlockPopup(id) {
      this.isOpen = id;
      this.selectedID = id;
    },
    saveTable(table) {
      addItemLS("table", this.tableData);
    },
  },

  watch: {
    addProduct() {
      this.tableData.push({
        id: this.tableData.length + 1,
        name: "",
        price: "",
        amount: "",
        type: "",
      });
    },
    tableData: {
      handler() {
        this.tableDataTotal.fullprice = this.tableData.reduce(
          (total, product) => {
            return (total += product.price * product.amount);
          },
          0
        );
        this.tableDataTotal.fullamount = this.tableData.reduce(
          (total, product) => {
            return (total += +product.amount);
          },
          0
        );
        this.tableDataTotal.weight = this.tableData.reduce((total, product) => {
          return (total +=
            +product.name
              .replace(new RegExp(`.*?, (.*)`), `$1`)
              .replace(/[^0-9]/g, "") * product.amount);
        }, 0);
      },
      deep: true,
    },
  },

  computed: {
    tableTitles() {
      return [
        "",
        "",
        "Наименование единицы",
        "Цена",
        "Кол-во",
        "Название товара",
        "Итого",
      ];
    },

    menuData() {
      return [
        "Отображение столбцов",
        "Фиксация столбцов",
        "Порядок столбцов",
        "Применить настройки для всех",
      ];
    },
  },
};
</script>
<style lang="scss" scoped>
@import "../assets/css/colors.scss";
.table-layot {
  position: relative;
  border-radius: 10px;
  box-shadow: 0 5px 20px 0 $black-7;
  border: solid 1px $pale-grey-two;
  background-color: $white;
  padding: 32px 0px 25px 0px;
}
.popup-setting {
  position: absolute;
  top: 9px;
  left: calc(100% - 30px);
}
.save {
  position: absolute;
  top: 10px;
  left: 1283px;
  font-family: "Myriad Pro", sans-serif;
  font-size: 12px;
  color: $light-grey-blue;
  cursor: pointer;
  transition: 0.3s;
  &:hover {
    transition: 0.3s;
    color: $light-navy;
  }
}
.fulltable {
  position: relative;
}
.table {
  display: grid;
  grid-template-columns: 50px 24px 624px 217px 217px 168px 149.5px;
  &__titles {
    border-top: 1px solid $pale-grey-two;
    border-bottom: 1px solid $pale-grey-two;
    border-left: 1px solid $pale-grey-two;
    padding: 14px 0px 14px 15px;
    font-family: "Myriad Pro", sans-serif;
    font-size: 16px;
    font-weight: 600;
    font-stretch: normal;
    font-style: normal;
    line-height: normal;
    letter-spacing: normal;
    color: $black;
  }

  &__elem {
    border-left: 1px solid $pale-grey-two;
    padding: 5px 15px 5px 15px;
    position: relative;
    &-inner {
      width: 100%;
      height: 35px;
      padding: 10px 0px 9px 15px;
      border-radius: 5px;
      border: solid 1px $pinkish-grey;
      background-color: $white;
      font-family: "Myriad Pro", sans-serif;
      font-size: 16px;
      font-weight: normal;
      font-stretch: normal;
      font-style: normal;
      letter-spacing: normal;
      color: $black;
      white-space: nowrap;
      overflow: hidden;
    }

    &-id {
      padding: 15px 0px 14px 31px;
      background-color: $white;
      font-family: "Myriad Pro", sans-serif;
      font-size: 16px;
      font-weight: normal;
      font-stretch: normal;
      font-style: normal;
      letter-spacing: normal;
    }

    &-to4ki {
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 16px 0px 16px 0px;
    }

    &-path {
      position: absolute;
      top: calc(0% + 6px);
      right: calc(0% + 16px);
      width: 21px;
      height: 33px;
      opacity: 0.9;
      border-radius: 4px;
      background-color: $white-two;
      display: flex;
      justify-content: center;
      align-items: center;
      img {
        width: 3px;
        height: 6px;
      }
      opacity: 1;
    }
  }
}
.flip-list-move {
  transition: transform 0.5s;
}
.ghost {
  position: relative;
  z-index: 2;
  &:before {
    content: " ";
    position: absolute;
    z-index: 2;
    top: 16px;
    left: 15px;
    width: 11px;
    height: 12px;
    background-image: url("../assets/image/SVG/12Combined Shape.svg");
  }
}

.point-hidden {
  height: 51.215px;
}
.page .sortable-drag {
  opacity: 0;
}
.v-enter-active {
  transition: 0.5s ease all;
}
.v-leave-active {
  transition: 0.2s ease all;
}
.v-enter-from,
.v-leave-to {
  opacity: 0;
  transform: translateY(-30px);
}
</style>
