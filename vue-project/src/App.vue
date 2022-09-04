<script setup lang="ts">
import IconStar from "@/components/IconStar.vue";
import { ref } from "vue";

const ratings = ref([1, 2, 3, 4, 5]);
const rate = ref(0);
const submitted = ref(false);

const selectRating = (r: number) => (rate.value = r);
</script>
<template>
  <div class="card flex flex-col" :class="{ 'justify-center': submitted }">
    <template v-if="!submitted">
      <div class="circle flex align-center">
        <IconStar class="mx-auto" />
      </div>
      <h2>How did we do?</h2>
      <p>
        Please let us know how we did with your support request. All feedback is
        appreciated to help us improve our offering!
      </p>
      <div class="flex justify-between">
        <button
          v-for="r in ratings"
          :key="r"
          class="rating circle"
          :class="{ 'rating--active': rate === r }"
          @click="selectRating(r)"
        >
          {{ r }}
        </button>
      </div>
      <button class="uppercase btn" @click="submitted = true">Submit</button>
    </template>
    <template v-else>
      <img src="./assets/images/illustration-thank-you.svg" alt="Thank you" />
      <div class="pill">You selected {{ rate }} out of 5</div>
      <h2>Thank you!</h2>
      <p>
        We appreciate you taking the time to give a rating. If you ever need
        more support, don’t hesitate to get in touch!
      </p>
    </template>
  </div>
</template>
