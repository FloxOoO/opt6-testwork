<template>
  <div class="menu">
    <draggable :list="menu" ghost-class="ghost">
      <transition-group type="transition" name="flip-list">
        <div v-for="point in menu" :key="point.id" class="title sortable">
          <div
            class="menu__container"
            @click.stop="openSubMenu(point.id)"
            :class="{
              title__active: opened === point.id,
            }"
          >
            <div class="title__hidden"></div>
            <div class="title__container">
              <div class="title__text">{{ point.title }}</div>
              <svg
                width="10px"
                height="17px"
                viewBox="0 0 10 17"
                version="1.1"
                xmlns="http://www.w3.org/2000/svg"
                xmlns:xlink="http://www.w3.org/1999/xlink"
                v-if="point.subtitles.length"
                class="path"
                src="../assets/image/SVG/21312431Path 4.svg"
                alt=""
                :class="{
                  path__open: opened === point.id,
                }"
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
                    id="iPhone-SE-Copy-32"
                    transform="translate(-355.000000, -31.000000)"
                    fill="#a6b7d4"
                  >
                    <g
                      id="Group-5"
                      transform="translate(281.000000, 31.000000)"
                    >
                      <path
                        d="M82.2806052,16.8130357 L74.1283815,8.78919338 C74.0427938,8.68220882 74,8.54312889 74,8.37195359 C74,8.20077828 74.0427938,8.06169835 74.1283815,7.95471379 L82.2806052,0.123443727 C82.7513373,-0.0905254 83.1792756,-0.0263346618 83.56442,0.316015942 C83.9495644,0.658366546 84.056549,1.0863048 83.8853737,1.59983071 L76.952774,8.33985822 L83.8853737,15.1440765 C84.0993428,15.6148085 84.0137552,16.0641437 83.6286107,16.492082 C83.2434663,16.9200202 82.7941311,17.0270048 82.2806052,16.8130357 Z"
                        id="Path-4"
                        transform="translate(79.000000, 8.460010) scale(-1, 1) translate(-79.000000, -8.460010) "
                      ></path>
                    </g>
                  </g>
                </g>
              </svg>
            </div>
          </div>
          <Transition>
            <div
              v-if="point.subtitles.length && opened === point.id"
              class="submenu"
            >
              <div
                v-for="(subtitle, id) in point.subtitles"
                :key="id"
                class="title__text title__active title__text-active"
              >
                {{ subtitle }}
              </div>
            </div>
          </Transition>
        </div>
      </transition-group>
    </draggable>
  </div>
</template>
<script>
import { VueDraggableNext } from "vue-draggable-next";
export default {
  name: "MainMenu",
  components: {
    draggable: VueDraggableNext,
  },

  data() {
    return {
      opened: null,
      menu: [
        {
          id: 0,
          title: "Логистика",
          subtitles: [],
        },
        {
          id: 1,
          title: "Перевозчики",
          subtitles: ["Перевозчики 1", "Перевозчики 2", "Перевозчики 3"],
        },
        {
          id: 2,
          title: "Задачи",
          subtitles: [],
        },
        {
          id: 3,
          title: "Аналитика",
          subtitles: ["Справочник", "База", "Ваза"],
        },
        {
          id: 4,
          title: "Адреса",
          subtitles: [],
        },
        {
          id: 5,
          title: "Товары",
          subtitles: [],
        },
        {
          id: 6,
          title: "Информация для склада",
          subtitles: [],
        },
        {
          id: 7,
          title: "Адреса",
          subtitles: [],
        },
      ],
    };
  },

  methods: {
    openSubMenu(id) {
      if (this.opened === id) {
        this.opened = null;
      } else {
        this.opened = id;
      }
    },
  },
};
</script>
<style lang="scss" scoped>
@import "../assets/css/colors.scss";
.menu {
  flex: 1 1 auto;
  margin-top: 81px;
  min-height: 719px;
  &__container {
    display: flex;
    position: relative;
    cursor: pointer;
    &:hover {
      .title__hidden {
        display: block;
      }
      .title__text {
        color: $pumpkin-orange;
      }
    }
  }
}
.title {
  &__container {
    display: flex;
    align-items: center;
    width: 229px;
    justify-content: space-between;
  }

  &__text {
    padding: 7px 0px 7px 25px;
    font-family: "Verdana", sans-serif;
    font-size: 14px;
    font-weight: normal;
    font-stretch: normal;
    font-style: normal;
    line-height: normal;
    letter-spacing: normal;
    color: $white;
    &-active {
      color: $light-grey-blue;
    }
  }

  &__hidden {
    display: none;
    position: absolute;
    top: 0;
    left: 0;
    width: 2px;
    height: 30px;
    background-color: $pumpkin-orange;
  }

  &__active {
    background-color: $dark-blue-grey;
  }
}
.path {
  width: 7px;
  height: 12px;
  margin-right: 17.5px;
  transform: rotate(90deg);
  cursor: pointer;
  &__open {
    transform: rotate(-90deg);
  }
}
.flip-list-move {
  transition: transform 0.5s;
}
.ghost {
  &:before {
    content: " ";
    position: absolute;
    z-index: 2;
    top: 10px;
    left: 9px;
    width: 11px;
    height: 12px;
    background-image: url("../assets/image/SVG/12Combined Shape.svg");
  }
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
