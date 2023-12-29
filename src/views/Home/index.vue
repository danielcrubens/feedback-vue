
<template>
  <custom-header @create-account="handleAccountCreate" @login="handleLogin" />
  <contact />
  <div class="flex justify-center py-5 bg-brand-gray">
    <p class="font-medium text-center text-gray-800">feedbacker © {{ currentYear }} </p>
  </div>
</template>

<script>
import { onMounted } from 'vue'
import { useRouter } from 'vue-router'
import Contact from './Contact.vue'
import CustomHeader from './CustomHeader.vue'

export default {
  components: { CustomHeader, Contact },
  setup () {
    const router = useRouter()

    onMounted(() => {
      const token = window.localStorage.getItem('token')
      if (token) {
        router.push({ name: 'Feedback' })
      }
    })
    // eslint-disable-next-line
    function handleLogin() { }
    // eslint-disable-next-line
    function handleAccountCreate() { }

    return {
      handleLogin,
      handleAccountCreate
    }
  },
  computed: {
    currentYear () {
      return new Date().getFullYear()
    }
  }
}
</script>
