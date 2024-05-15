<template>
  <div class="app">
    <header>
      <div class="order">
        <button @click="handleClick('title')">주문하기 제목</button>
        <button @click="handleClick('salary')">주문하기 급여</button>
        <button @click="handleClick('location')">주문하기 지역</button>
      </div>
    </header>
    <!-- props로 전달 -->
    <JobList :jobs="jobs" :order="order" />
  </div>
</template>
./types/Job
<script lang="ts">
import { defineComponent, reactive, ref, toRefs } from "vue";
import Job from "./types/Job";
import OrderTerm from "./types/OrderTerm";
import JobList from "./components/JobsList.vue";

export default defineComponent({
  name: "App",
  components: {
    JobList,
  },
  setup() {
    const jobs = ref<Job[]>([
      {
        title: "농장근로자",
        location: "서울 지역",
        salary: 300000000,
        id: "2",
      },
      {
        title: "사무실근로자",
        location: "전라도 지역",
        salary: 350000000,
        id: "3",
      },
      {
        title: "현장근로자",
        location: "충청도 지역",
        salary: 300000000,
        id: "4",
      },
      {
        title: "어부",
        location: "전라남도 지역",
        salary: 300000000,
        id: "5",
      },
      {
        title: "광산근로자",
        location: "강원도 지역",
        salary: 600000000,
        id: "6",
      },
    ]);

    const order = ref<OrderTerm>("title");
    const handleClick = (term: OrderTerm) => {
      order.value = term;
    };
    return { jobs, handleClick, order };
  },
});
</script>

<style>
</style>