<template>
  <div>
    <Level :levelId="id" v-on:checkResult="updateComplete" />
    <Hud
      :levelTitle="title"
      :levelSubtitle="subtitle"
      :infoItems="axioms"
      :lastName="last"
      :nextName="next"
    />
  </div>
</template>

<script>
import Level from "../../../components/Level.vue";
import Hud from "../../../components/Hud.vue";

export default {
  name: "B1",
  components: {
    Level,
    Hud
  },
  data() {
    return {
      id: "1-1",
      title: "Beginner 1",
      subtitle: "3 Point Geometry",
      last: "T2",
      next: "B2",
      axioms: [
        {
          objective: 1,
          description: "There exist exactly three points.",
          complete: false
        },
        {
          objective: 2,
          description: "Two distinct points are on exactly one line",
          complete: false
        },
        {
          objective: 3,
          description: "Not all the three points are collinear.",
          complete: false
        },
        {
          objective: 4,
          description: "Two distinct lines are on at least one point.",
          complete: false
        }
      ]
    };
  },
  mounted() {},
  methods: {
    updateComplete(result) {
      for (let a of this.axioms) {
        a.complete = result[a.objective - 1];
      }
    }
  }
};
</script>
