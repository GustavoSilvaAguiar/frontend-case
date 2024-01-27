<template>
  <div class="sideBar" :class="sideBarClosed ? 'sideBarClosed' : ''">
    <div>
      <div class="sideBar--header" @click="openAndCloseSideBar">
        <img src="../../assets/images/logo.svg" />
        <div :class="sideBarClosed ? 'closed' : ''">
          <strong class="sideBar--header--jurisoft">Jurisoft</strong>
          <div class="sideBar--header--sub">Marketing Jurídico</div>
        </div>
        <img
          :class="sideBarClosed ? 'closed' : ''"
          src="../../assets/icons/arrow-down-s-line.svg"
        />
      </div>
      <div class="sideBar--divider" />
      <div class="sideBar--title">main</div>
      <div>
        <SideBarButton :closed="sideBarClosed" title="Dashboard" url="/">
          <GridIcon class="icon"
        /></SideBarButton>
        <SideBarButton :closed="sideBarClosed" title="Calendário" url="calendario">
          <calendarIconVue class="icon"
        /></SideBarButton>
        <SideBarButton :closed="sideBarClosed" title="Descanso" url="default">
          <clockIconVue class="icon"
        /></SideBarButton>
        <SideBarButton :closed="sideBarClosed" title="Projetos" url="default">
          <folderIconVue class="icon"
        /></SideBarButton>
        <SideBarButton :closed="sideBarClosed" title="Times" url="default">
          <groupIconVue class="icon"
        /></SideBarButton>
        <SideBarButton :closed="sideBarClosed" title="Integrações" url="default">
          <equalizerIconVue class="icon"
        /></SideBarButton>
        <SideBarButton :closed="sideBarClosed" title="Benefícios" url="default">
          <starSmileIconVue class="icon"
        /></SideBarButton>
        <SideBarButton :closed="sideBarClosed" title="Documentos" url="default">
          <fileCludIconVue class="icon"
        /></SideBarButton>
      </div>

      <div class="sideBar--title">favs</div>
      <div>
        <div class="sideBar--favsWrap">
          <div class="sideBar--favsWrap--ball--1 sideBar--favsWrap--ball" />
          <div
            :class="sideBarClosed ? 'closed' : ''"
            class="sideBar--favsWrap--text"
          >
            Loom Mobile App
          </div>
          <div
            :class="sideBarClosed ? 'closed' : ''"
            class="sideBar--favsWrap--icon"
          >
            ⌘ 1
          </div>
        </div>
        <div class="sideBar--favsWrap">
          <div class="sideBar--favsWrap--ball--2 sideBar--favsWrap--ball" />
          <div
            :class="sideBarClosed ? 'closed' : ''"
            class="sideBar--favsWrap--text"
          >
            Monday Redesign
          </div>
          <div
            :class="sideBarClosed ? 'closed' : ''"
            class="sideBar--favsWrap--icon"
          >
            ⌘ 2
          </div>
        </div>
        <div class="sideBar--favsWrap">
          <div class="sideBar--favsWrap--ball--3 sideBar--favsWrap--ball" />
          <div
            :class="sideBarClosed ? 'closed' : ''"
            class="sideBar--favsWrap--text"
          >
            Udemy Courses
          </div>
          <div
            :class="sideBarClosed ? 'closed' : ''"
            class="sideBar--favsWrap--icon"
          >
            ⌘ 3
          </div>
        </div>
      </div>
    </div>
    <div>
      <div class="sideBar--helpers">
        <img src="../../assets/icons/settings-2-line.svg" />
        <span :class="sideBarClosed ? 'closed' : ''">Configurações</span>
      </div>
      <div class="sideBar--helpers">
        <img src="../../assets/icons/headphone-line.svg" />
        <span :class="sideBarClosed ? 'closed' : ''">Suporte</span>
      </div>
      <div class="sideBar--divider" />
      <div class="sideBar--account">
        <div>
          <img
            src="../../assets/images/Avatar.png"
            height="40px"
            width="40px"
          />
          <img
            :class="!sideBarClosed ? 'closed' : ''"
            class="imgStatus"
            src="../../assets/icons/topStatus.svg"
            height="18px"
            width="18px"
          />
        </div>

        <div :class="sideBarClosed ? 'closed' : ''">
          <div class="sideBar--account--title">
            Sophia Williams
            <img
              src="../../assets/icons/topStatus.svg"
              height="18px"
              width="18px"
            />
          </div>
          <div class="sideBar--account--subtitle">sophia@jurisoft.com</div>
        </div>
        <img
          :class="sideBarClosed ? 'closed' : ''"
          src="../../assets/icons/arrow-right-s-line.svg"
        />
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
import calendarIconVue from "~/assets/icons/calendarIcon.vue";
import clockIconVue from "~/assets/icons/clockIcon.vue";
import folderIconVue from "~/assets/icons/folderIcon.vue";
import GridIcon from "~/assets/icons/gridIcon.vue";
import groupIconVue from "~/assets/icons/groupIcon.vue";
import equalizerIconVue from "~/assets/icons/equalizerIcon.vue";
import starSmileIconVue from "~/assets/icons/starSmileIcon.vue";
import fileCludIconVue from "~/assets/icons/fileCloudIcon.vue";

const sideBarClosed = ref<boolean>(true);

const openAndCloseSideBar = () => {
  sideBarClosed.value = !sideBarClosed.value;
};
</script>

<style lang="scss" scoped>
.sideBar {
  transition: all 0.15s;
  width: 272px;
  border-right: 1px solid #e2e4e9;
  overflow-x: hidden;
  overflow-y: auto;
  display: flex;
  flex-direction: column;
  justify-content: space-between;

  &--header {
    cursor: pointer;
    display: grid;
    grid-template-columns: auto 1fr auto;
    align-items: center;
    padding: 12px;
    column-gap: 12px;
    &--jurisoft {
      font-size: 14px;
      font-style: normal;
      font-weight: 500;
      line-height: 20px;
      letter-spacing: -0.084px;
    }
    &--sub {
      font-size: 12px;
      font-style: normal;
      font-weight: 400;
      line-height: 16px;
    }
  }

  &--divider {
    margin: 0px 20px;
    height: 1px;
    background-color: #e2e4e9;
  }

  &--title {
    font-size: 12px;
    font-style: normal;
    font-weight: 500;
    line-height: 16px;
    letter-spacing: 0.48px;
    text-transform: uppercase;
    color: $light-gray;
    margin-top: 20px;
    margin-bottom: 5px;
    padding: 0px 20px;
  }

  &--btn {
    &--btnBody {
      &:hover,
      &--selecionado {
        .icon {
          fill: $primary;
        }
      }
    }
  }

  &--favsWrap {
    display: grid;
    grid-template-columns: auto 1fr auto;
    align-items: center;
    column-gap: 8px;
    padding: 8px 32px;

    &--ball {
      border-radius: 100%;
      width: 10px;
      height: 10px;

      &--1 {
        background-color: #6e3ff3;
      }
      &--2 {
        background-color: #df1c41;
      }
      &--3 {
        background-color: #e255f2;
      }
    }

    &--text {
      font-size: 14px;
      font-weight: 500;
      line-height: 20px;
      letter-spacing: -0.084px;
      color: #525866;
    }

    &--icon {
      border-radius: 4px;
      border: 1px solid #e2e4e9;
      padding: 0px 6px;
      color: #868c98;
      font-size: 14px;
      font-weight: 500;
      line-height: 20px;
      letter-spacing: -0.084px;
    }
  }

  &--helpers {
    display: grid;
    grid-template-columns: auto 1fr;
    align-items: center;
    padding: 8px 28px;
    margin-left: auto;
    margin-right: auto;
    column-gap: 8px;
    font-size: 14px;
    font-style: normal;
    font-weight: 500;
    color: #525866;
    cursor: pointer;
    width: 80%;

    &:hover {
      border-radius: 8px;
      background-color: #f6f8fa;
    }
  }

  &--account {
    display: grid;
    grid-template-columns: auto 1fr auto;
    align-items: center;
    column-gap: 12px;
    padding: 8px 16px;

    &--title {
      display: flex;
      align-items: center;
      font-size: 14px;
      font-weight: 500;
      color: #0a0d14;
    }
    &--subtitle {
      font-size: 12px;
      font-weight: 400;
      color: #525866;
    }
  }
}
.sideBarClosed {
  width: 80px;

  .sideBar--header {
    display: flex;
    justify-content: center;
  }
}
.closed {
  display: none;
}
.imgStatus {
  position: relative;
  left: 28px;
  bottom: 43px;
}
</style>
