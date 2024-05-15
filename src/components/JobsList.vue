<template>
  <div class="job-list">
    <p>{{ order }}로 주문하기</p>
    <ul>
      <li v-for="job in orderedJobs" :key="job.id">
        <h2>{{ job.title }} in {{ job.location }}</h2>
        <div class="salary">
          <p>{{ job.salary }} 원</p>
        </div>
        <div class="description">
          <p>
            보안인증을 진행해야만 티비위키에 접속 하실 수 있습니다. 모바일앱 ,
            스마트티비 환경에서는 인증이 안될 수 있으니 일반 웹브라우저로 접속
            부탁드립니다. 인증이 어려운 사용자께서는 잠시 후 다시 시도 해주시길
            바랍니다.
          </p>
        </div>
      </li>
    </ul>
  </div>
</template>
<script lang="ts">
import { computed, defineComponent, PropType } from "vue";
import Job from "../types/Job";
import OrderTerm from "../types/OrderTerm";

export default defineComponent({
  props: {
    jobs: {
      required: true,
      type: Array as PropType<Job[]>,
    },
    order: {
      required: true,
      type: String as PropType<OrderTerm>,
    },
  },
  setup(props) {
    const orderedJobs = computed(() => {
      return [...props.jobs].sort((a: Job, b: Job) => {
        return a[props.order] > b[props.order] ? 1 : -1;
      });
    });
    return { orderedJobs };
  },
});
</script>
<style scoped>
</style>
