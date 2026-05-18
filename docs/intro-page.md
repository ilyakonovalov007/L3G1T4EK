---
layout: page
---

<div class="intro-container" v-show="!isLoading">
  <div class="intro-header">
    <h1 class="intro-title">Добро пожаловать!</h1>
  </div>

  <div class="content-box">
    <p class="intro-text">
      <strong>Прежде чем переходить к обучению</strong>, давайте коротко определим, что мы сегодня понимаем под социальными сетями. Это уже не просто площадки для обмена сообщениями и фотографиями. Современная социальная сеть - многофункциональная платформа, которая объединяет в себе элементы мессенджера, видеохостинга, сайта знакомств и даже маркетплейса.
    </p>
    <p class="intro-text">
      Соцсети остаются базовой площадкой для общения, но на первый план выходят другие функции:
    </p>
    <ul class="features-list">
      <li>
        <span class="icon">📱</span>
        <div>
          <strong>Потребление контента.</strong> Короткие видео, стримы, длинные тексты и подкасты.
        </div>
      </li>
      <li>
        <span class="icon">📰</span>
        <div>
          <strong>Чтение новостей.</strong> Для многих россиян лента в популярных соцсетях стала главным источником информации.
        </div>
      </li>
      <li>
        <span class="icon">🛒</span>
        <div>
          <strong>Покупки и бизнес.</strong> От рекламы в блогерских каналах до полностью интегрированных магазинов.
        </div>
      </li>
      <li>
        <span class="icon">🤝</span>
        <div>
          <strong>Работа и нетворкинг.</strong> Профессиональные связи все чаще перемещаются в российские соцсети и мессенджеры.
        </div>
      </li>
    </ul>
    <button @click="markAsRead" class="read-btn">
      Прочитал
    </button>
  </div>
</div>

<script setup>
import { ref, onMounted } from 'vue'

const isLoading = ref(true)

onMounted(() => {
  if (typeof window !== 'undefined') {
    // Проверяем, читал ли пользователь это ранее
    const isRead = localStorage.getItem('intro_read_completed') === 'true'
    
    if (isRead) {
      // Если читал - сразу перекидываем на ВКонтакте
      window.location.href = '/vk-info'
    } else {
      // Если нет - показываем страницу
      isLoading.value = false
    }
  }
})

const markAsRead = () => {
  if (typeof window !== 'undefined') {
    localStorage.setItem('intro_read_completed', 'true')
    window.location.href = '/vk-info'
  }
}
</script>

<style scoped>
.intro-container {
  max-width: 800px;
  margin: 0 auto;
  padding: 2rem 20px;
  animation: fadeIn 0.5s ease-out;
}

.intro-header {
  text-align: center;
  margin-bottom: 2rem;
}

.intro-title {
  font-size: 2.8rem;
  font-weight: 800;
  background: linear-gradient(120deg, #3b82f6, #8b5cf6);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  display: inline-block;
  margin: 0;
  line-height: 1.2;
  letter-spacing: normal;
}

.content-box {
  background: var(--vp-c-bg-soft);
  border: 1px solid var(--vp-c-divider);
  border-radius: 16px;
  padding: 30px;
  box-shadow: 0 10px 30px rgba(0,0,0,0.05);
}

.intro-text {
  font-size: 1.15rem;
  line-height: 1.7;
  color: var(--vp-c-text-1);
  margin-bottom: 1.5rem;
}

.features-list {
  list-style: none;
  padding: 0;
  margin: 2rem 0;
  display: flex;
  flex-direction: column;
  gap: 15px;
}

.features-list li {
  display: flex;
  align-items: flex-start;
  gap: 15px;
  background: var(--vp-c-bg-alt);
  padding: 15px 20px;
  border-radius: 12px;
  border: 1px solid var(--vp-c-divider);
  font-size: 1.05rem;
  line-height: 1.5;
}

.features-list .icon {
  font-size: 1.5rem;
}

.read-btn {
  display: block;
  width: 100%;
  padding: 16px;
  font-size: 1.2rem;
  font-weight: bold;
  color: white;
  background: #10b981;
  border: none;
  border-radius: 12px;
  cursor: pointer;
  transition: all 0.2s ease;
  margin-top: 10px;
}

.read-btn:hover {
  background: #059669;
  transform: translateY(-2px);
  box-shadow: 0 5px 15px rgba(16, 185, 129, 0.3);
}

@keyframes fadeIn {
  from { opacity: 0; transform: translateY(10px); }
  to { opacity: 1; transform: translateY(0); }
}
</style>