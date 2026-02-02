<template>
  <div>
    <TheHeader />
    <BadgeList />
    <UserInfo
      :full-name="activeUser.name"
      :info-text="activeUser.description"
      :role="activeUser.role"
    ></UserInfo>
    <base-card>
      <CourseGoals>
        <template #default="slotProps"
          ><h2>{{ slotProps.item }}</h2></template
        >
      </CourseGoals>
    </base-card>
    <base-card>
      <button @click="setSelectedComponent('active-goals')">
        Active goals
      </button>
      <button @click="setSelectedComponent('manage-goals')">
        Manage goals
      </button>
    </base-card>
    <base-card v-if="selectedComponent === 'active-goals'"
      ><ActiveGoals></ActiveGoals
    ></base-card>
    <base-card v-if="selectedComponent === 'manage-goals'"
      ><ManageGoals> </ManageGoals
    ></base-card>
    <base-card>
      <keep-alive>
        <component :is="selectedComponent"> </component>
      </keep-alive>
    </base-card>
  </div>
</template>

<script>
import ActiveGoals from "./components/ActiveGoals.vue";
import ManageGoals from "./components/ManageGoals.vue";
import BadgeList from "./components/BadgeList.vue";
import CourseGoals from "./components/CourseGoals.vue";
import TheHeader from "./components/TheHeader.vue";
import UserInfo from "./components/UserInfo.vue";

export default {
  components: {
    TheHeader,
    BadgeList,
    UserInfo,
    CourseGoals,
    ActiveGoals,
    ManageGoals,
  },
  data() {
    return {
      selectedComponent: "active-goals",
      activeUser: {
        name: "Maximilian Schwarzmüller",
        description: "Site owner and admin",
        role: "admin",
      },
    };
  },
  methods: {
    setSelectedComponent(componentName) {
      this.selectedComponent = componentName;
    },
  },
};
</script>

<style>
html {
  font-family: sans-serif;
}

body {
  margin: 0;
}
</style>
