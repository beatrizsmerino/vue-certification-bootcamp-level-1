<script setup>
import { computed, ref } from "vue";

const emit = defineEmits({
  "update:username": (payload) => {
    return payload !== "";
  },
});

const props = defineProps({
  avatar: {
    type: String,
    default: "/placeholder-avatar.jpg",
  },
  username: {
    type: String,
    required: true,
  },
  bio: {
    type: String,
    default: "",
  },
  name: {
    type: Object,
    default: () => ({ first: "John", last: "Doe" }),
  },
  skills: {
    type: Array,
    default: () => [],
    validator: (skills) => {
      return skills.length > 0;
    },
  },
  pro: {
    type: Boolean,
    default: false,
  },
});

function updateUsername(username) {
  emit(
    "update:username",
    username.replace(/^@/, "").replace(/[^a-zA-Z0-9]/g, ""),
  );
}

const usernameWithAt = computed(() => {
  return `@${props.username}`;
});

const skillsInOrder = computed(() => {
  return [...props.skills].sort((a, b) => a.localeCompare(b));
});
</script>
<template>
  <div class="profile-card">
    <div class="header">
      <span v-if="pro" class="badge">PRO</span>
      <div class="avatar-wrapper">
        <img :src="avatar" :alt="`${name.first} ${name.last}`" class="avatar" />
      </div>
    </div>
    <div class="body">
      <h3 class="name">{{ name.first }} {{ name.last }}</h3>
      <h4 class="username">
        <input
          type="text"
          :value="usernameWithAt"
          @input="updateUsername($event.target.value)"
        />
      </h4>
      <p class="bio">{{ bio }}</p>
      <div class="actions">
        <button class="message-btn">Message</button>
        <button class="follow-btn">Follow</button>
      </div>
    </div>
    <div class="footer">
      <ul class="skills">
        <li v-for="skill in skillsInOrder" :key="skill">{{ skill }}</li>
      </ul>
    </div>
  </div>
</template>

<style scoped>
/* Card Design based on this article from Florin Pop
www.florin-pop.com/blog/2019/04/profile-card-design/
*/
.profile-card {
  @apply bg-white dark:bg-base-200 rounded-lg overflow-hidden shadow-md max-w-xs;
}

.header {
  @apply bg-blue-500 p-4 text-white relative;
}

.badge {
  @apply absolute top-2 right-2 bg-yellow-300 text-yellow-800 py-1 px-2 rounded text-xs;
}

.avatar-wrapper {
  @apply flex justify-center;
}

.avatar {
  @apply rounded-full border-4 border-white h-24 w-24 object-cover;
}

.body {
  @apply p-4 text-center;
}

.name {
  @apply text-lg font-bold;
}

.username {
  @apply text-gray-500 text-sm;
}

.username input {
  @apply bg-transparent w-auto inline-block min-w-0 text-center;
}

.bio {
  @apply text-gray-700 my-2 dark:text-gray-500;
}

.actions {
  @apply flex justify-center mt-4 gap-3;
}

.message-btn,
.follow-btn {
  @apply bg-blue-500 text-white py-2 px-4 rounded hover:bg-blue-600 focus:outline-none focus:ring-2 focus:ring-blue-300;
}

.footer {
  @apply bg-gray-100 p-4 flex justify-center dark:bg-base-300;
}

.skills {
  @apply list-none flex flex-wrap justify-center gap-2 items-center;
}

.skills li {
  @apply bg-gray-200 text-gray-800 py-1 px-2 rounded text-xs dark:bg-base-100 dark:text-gray-300;
}
</style>
