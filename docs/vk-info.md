---
layout: page
---

<div class="hero-section">
  <div class="hero-content-wrapper">
    <div class="hero-text">
      <h1 class="hero-title">Безопасность ВКонтакте</h1>
      <p class="hero-subtitle">Интерактивный мини-курс по защите вашей личной страницы</p>
      <h3 style="font-size: 1.4rem; font-weight: 700; margin-top: 20px; margin-bottom: 10px; color: var(--vp-c-text-1);">
    Почему важно защитить свой аккаунт?
  </h3>
      <div class="hero-description">
      <p style="font-size: 0.95rem; color: var(--vp-c-text-2); margin-bottom: 15px; font-style: italic;">
      <br>
    * <b>Фишинговая атака (фишинг)</b> — это вид интернет-мошенничества, когда злоумышленники создают поддельные сайты, точь-в-точь похожие на настоящие (например, на страницу входа ВКонтакте). Их цель — обманом заставить вас ввести свой логин и пароль, чтобы получить доступ в ваш аккаунт.
  </p>
      <br>
        По данным Минцифры и Сбербанка за <b>конец 2025 — начало 2026 года</b>, социальные сети стали основным местом для киберпреступников в РФ: <b>больше половины всех  * фишинговых атак</b> направлены на угон аккаунтов. ВКонтакте пользуются более 90 миллионов человек в месяц. Для людей в возрасте 35–45 лет профиль — это личное пространство, где хранятся личные переписки, контакты близких и привязанные платёжные сервисы. Получение доступа в аккаунт приводит к финансовым потерям и репутационному ущербу.
      </div>
      <p class="hero-action">Выберите тему ниже, чтобы начать обучение:</p>
    </div>
    <div class="hero-image-side">
      <img src="/stats35.jpg" alt="Распределение аудитории ВКонтакте">
    </div>
  </div>
</div>

---

<div class="sub-topics-grid">
  
  <!-- Ветка 1: Распознавание мошенника -->
  <a href="/vk/fake_profiles" class="topic-card">
    <div class="topic-icon">🕵️</div>
    <div class="topic-content">
      <h3>
        Как распознать мошенника 
        <span v-if="isFakeProfileDone" class="status-badge">✅ Пройдено</span>
      </h3>
      <p>Учимся вычислять злоумышленников по постановочным фото, странным репостам и списку друзей.</p>
    </div>
    <div class="topic-arrow">→</div>
  </a>

  <!-- Ветка 2: Настройки приватности -->
  <a href="/vk/privacy" class="topic-card">
    <div class="topic-icon">👁️</div>
    <div class="topic-content">
      <h3>
        Настройки приватности
        <span v-if="isPrivacyDone" class="status-badge">✅ Пройдено</span>
      </h3>
      <p>Как скрыть фото, друзей и активность, чтобы лишить злоумышленника возможности собрать о вас информацию.</p>
    </div>
    <div class="topic-arrow">→</div>
  </a>

  <!-- Ветка 3: 2FA и Активные сессии -->
  <a href="/vk/sessions" class="topic-card">
    <div class="topic-icon">📱</div>
    <div class="topic-content">
      <h3>
        2FA и Активные сессии
        <span v-if="isSessionsDone" class="status-badge">✅ Пройдено</span>
      </h3>
      <p>Настройка двухфакторной аутентификации и контроль устройств, с которых входили в ваш аккаунт.</p>
    </div>
    <div class="topic-arrow">→</div>
  </a>

</div>

<script setup>
import { ref, onMounted } from 'vue'

const isFakeProfileDone = ref(false)
const isPrivacyDone = ref(false)
const isSessionsDone = ref(false)

onMounted(() => {
  if (typeof window !== 'undefined') {
    // ЗАМЕНЕНО НА sessionStorage: теперь статусы динамически обновляются при перезагрузке сессии
    isFakeProfileDone.value = sessionStorage.getItem('lesson_vk_fake_completed') === 'true'
    isPrivacyDone.value = sessionStorage.getItem('lesson_vk_privacy_completed') === 'true'
    isSessionsDone.value = sessionStorage.getItem('lesson_vk_sessions_completed') === 'true'
  }
})
</script>

<style scoped>
/* 1. ГЛОБАЛЬНЫЙ ЦЕНТРИРУЮЩИЙ КОНТЕЙНЕР ДЛЯ ВСЕЙ СТРАНИЦЫ */
.hero-section, 
.sub-topics-grid {
  max-width: 1100px !important; /* Не дает странице разъезжаться шире 1100px на ПК */
  margin-left: auto !important;   /* Магия центрирования: левое поле автоматическое */
  margin-right: auto !important;  /* Магия центрирования: правое поле автоматическое */
  padding: 0 20px;               /* Отступы, чтобы на телефонах текст не прилипал к краям */
}

.hero-section {
  padding-top: 1.5rem;
  padding-bottom: 2rem;
}

/* 2. ХЕДЕР СТРАНИЦЫ (ТЕКСТ + КАРТИНКА) */
.hero-content-wrapper {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 50px;
  margin-bottom: 2.5rem;
}

.hero-text {
  flex: 1.2;
  max-width: 650px;
}

.hero-title {
  font-size: 3rem;
  font-weight: 800;
  line-height: 1.2;
  margin-bottom: 0.5rem;
  background: linear-gradient(120deg, #4c75a3, #2787f5);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.hero-subtitle {
  font-size: 1.4rem;
  font-weight: 600;
  color: var(--vp-c-text-1);
  margin-bottom: 1.5rem;
}

.hero-description {
  font-size: 1.15rem;
  line-height: 1.6;
  color: var(--vp-c-text-2);
  margin-bottom: 2rem;
  text-align: justify; /* Чтобы текст смотрелся аккуратно и ровно */
}

.hero-action {
  font-weight: 700;
  color: var(--vp-c-brand);
  text-transform: uppercase;
  letter-spacing: 1px;
  font-size: 0.9rem;
}

/* Блок картинки */
.hero-image-side {
  flex: 1;
  display: flex;
  justify-content: flex-end;
}

.hero-image-side img {
  width: 100%;
  max-width: 500px; /* Немного уменьшили максимальную ширину для баланса */
  height: auto;
  border-radius: 16px;
  box-shadow: 0 12px 36px rgba(0,0,0,0.08); 
  border: 1px solid var(--vp-c-divider);
}

/* 3. СЕТКА С КАРТОЧКАМИ ТЕМ */
.sub-topics-grid { 
  display: flex; 
  flex-direction: column; 
  gap: 20px; 
  margin-top: 1rem; 
  margin-bottom: 3rem;
}

.topic-card {
  display: flex;
  align-items: center;
  gap: 20px;
  padding: 24px;
  background: var(--vp-c-bg-soft);
  border-radius: 16px;
  border: 1px solid var(--vp-c-divider);
  text-decoration: none;
  color: var(--vp-c-text-1);
  transition: all 0.3s cubic-bezier(0.25, 0.8, 0.25, 1);
}

.topic-card:hover:not(.coming-soon) {
  border-color: #2787f5;
  background: var(--vp-c-bg-alt);
  transform: translateY(-2px);
  box-shadow: 0 10px 20px rgba(0,0,0,0.05);
}

.topic-icon { 
  font-size: 2.8rem; 
  width: 60px; 
  text-align: center; 
}

.topic-content h3 { 
  margin: 0 0 4px 0; 
  font-size: 1.3rem; 
  color: #2787f5; 
  font-weight: 700; 
}

.topic-content p { 
  margin: 0; 
  font-size: 1rem; 
  color: var(--vp-c-text-2); 
}

.status-badge {
  font-size: 0.8rem;
  background: rgba(16, 185, 129, 0.15);
  color: #10b981;
  padding: 2px 8px;
  border-radius: 12px;
  margin-left: 10px;
  vertical-align: middle;
  font-weight: 600;
}

/* 4. 📱 АДАПТИВНОСТЬ ПОД МАСШТАБ И МОБИЛКИ */
@media (max-width: 960px) {
  .hero-content-wrapper {
    flex-direction: column-reverse; /* Картинка падает под текст при зуме или на смартфонах */
    align-items: center;
    gap: 30px;
  }
  .hero-text {
    max-width: 100%;
  }
  .hero-title { 
    font-size: 2.2rem; 
    text-align: center;
  }
  .hero-subtitle {
    text-align: center;
  }
  .hero-image-side { 
    justify-content: center; 
    width: 100%; 
  }
}

@media (max-width: 576px) {
  .topic-card {
    flex-direction: column; /* Карточки на мелких телефонах становятся вертикальными */
    text-align: center;
    padding: 20px;
  }
  .topic-icon {
    font-size: 3rem;
    width: 100%;
  }
}
</style>