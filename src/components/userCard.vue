<template>
  <div class="user-card">
    <h1>Научу зарабатывать от 50 000р. в час</h1>
    <div class="main-information">
      <img src="../assets/man.jpg" alt width="500px" />
      <div class="info">
        <h2>{{ getAuthorFullName }}</h2>
        <strong>Бизнес-коуч</strong>
        <ul>
          <li>Учу людей делать РЕАЛЬНЫЕ бабки, на себя просто не хватило времени Х(</li>
          <li>Не знаю, что такое "Успешный Успех", но знаю, что нужно ТЕБЕ!</li>
          <li>Пообещал, что побреюсь, когда кого-нибудь ОБМАНУ</li>
        </ul>
      </div>
    </div>
    <p>Участников: {{ users.length }}</p>
    <ul>
      <li v-for="(user, index) in users" :key="index">{{ `${index + 1}. ${getFullName(user)}` }}</li>
    </ul>
    <button type="button" :disabled="currentPage == 1" @click="currentPage--">Пред.</button>
    <button type="button" v-for="page in pages" :key="page" @click="currentPage = page">{{ page }}</button>
    <button type="button" :disabled="currentPage == pages" @click="currentPage++">След.</button>
    <p>Страница {{ currentPage }} из {{ pages }}</p>
  </div>
</template>

<script>
export default {
  name: "userCard",
  data() {
    return {
      firstName: "Игнатий",
      secondName: "Илларионович",
      lastName: "Богатов",
      users: [
        {
          firstName: "Игнатий",
          secondName: "Иларионович",
          lastName: "Богатов",
        },
        {
          firstName: "Иван",
          secondName: "Иванович",
          lastName: "Иванов",
        },
        {
          firstName: "Петр",
          secondName: "Петрович",
          lastName: "Петров",
        },
      ],
      pages: 3,
      currentPage: 1,
    };
  },

  computed: {
    getAuthorFullName() {
      return `${this.firstName} ${this.secondName} ${this.lastName}`.toUpperCase();
    },
  },
  methods: {
    getFullName(user) {
      return `${user.firstName} ${user.secondName} ${user.lastName}`;
    },
    loadUsers(page) {
      console.log(`Загрузка пользователей: страница ${page}`);
    },
  },
  watch: {
    currentPage(page) {
      this.loadUsers(page);
    },
  },
};
</script>
<style lang="scss" scoped>
.user-card {
  margin-top: 40px;
}

.info {
  margin-left: 50px;
}

h2 {
  margin-bottom: 14px;
}
</style>