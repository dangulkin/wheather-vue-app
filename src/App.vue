<script setup lang="ts">
import { ref } from "vue";

const searchInput = ref("");

const logInput = () => {
  console.log(searchInput.value);
};

const handleSubmit = (e: Event) => {
  e.preventDefault();
  logInput();
};
</script>

<template>
  <div class="content">
    <header class="header">
      <img class="logo" src="./assets/images/logo.svg" alt="logo" />
      <label class="search">
        <input class="search__input" type="text" placeholder="Поиск по городу" v-model="searchInput"
          @input="logInput" />
        <button type="submit" class="search__btn" @click="handleSubmit" v-show="searchInput != ''"></button>
      </label>
    </header>
    <main class="main">
      <div class="forecast">
        <div class="forecast__city-info">
          <span class="forecast__city">Москва</span>
          <p class="forecast__date">Суббота, 06 января</p>
          <p class="forecast__time">11:29</p>
        </div>
        <span class="forecast__temperature">-7°</span>
        <div class="forecast__other-info">
          <div class="forecast__conditions">
            <img class="forecast__icon" alt="weather icon" src="./assets/images/day-broken-clouds.png" />
            <p>Облачно</p>
          </div>
          <p class="forecast__feels">Ощущается как -11°</p>
        </div>
      </div>
      <div class="cards">
        <ul class="cards__list">
          <li class="card humidity">
            <span class="card__label">Влажность</span>
            <i class="card__icon"></i>
            <p class="card__value">75 %</p>
            <div class="bar">
              <div class="bar__progress">
                <div class="bar__thumb"></div>
              </div>
              <div class="bar__descr">
                <p class="bar__min">0%</p>
                <p class="bar__text"></p>
                <p class="bar__max">100%</p>
              </div>
            </div>
          </li>
          <li class="card pressure">
            <span class="card__label">Давление</span>
            <i class="card__icon"></i>
            <p class="card__value">761</p>
            <div class="bar">
              <div class="bar__progress">
                <div class="bar__thumb"></div>
              </div>
              <div class="bar__descr">
                <p class="bar__text">Повышенное</p>
              </div>
            </div>
          </li>
          <li class="card visibility">
            <span class="card__label">Видимость</span>
            <i class="card__icon"></i>
            <p class="card__value">28 км</p>
            <div class="bar">
              <div class="bar__progress">
                <div class="bar__thumb"></div>
              </div>
              <div class="bar__descr">
                <p class="bar__text">Нормальная</p>
              </div>
            </div>
          </li>
          <li class="card sunrise">
            <span class="card__label">Рассвет</span>
            <i class="card__icon"></i>
            <p class="card__value">8:42</p>
            <div class="bar">
              <div class="bar__descr">
                <p class="bar__text">Прошло 02:47</p>
              </div>
            </div>
          </li>
          <li class="card sunset">
            <span class="card__label">Закат</span>
            <i class="card__icon"></i>
            <p class="card__value">16:37</p>
            <div class="bar">
              <div class="bar__descr">
                <p class="bar__text">Осталось 05:08</p>
              </div>
            </div>
          </li>
          <li class="card wind">
            <span class="card__label">Сила ветра</span>
            <i class="card__icon"></i>
            <p class="card__value">2 м/с</p>
            <div class="bar">
              <div class="bar__descr">
                <p class="bar__text">Северо-западный</p>
              </div>
            </div>
          </li>
        </ul>
      </div>
    </main>
    <div class="slider"></div>
    <footer class="footer"></footer>
  </div>
</template>

<style scoped>
.content {
  width: 1120px;
  border-radius: 8px;
  background-color: var(--content-bg);
  backdrop-filter: blur(25px);
  margin: 32px auto;
}

.header {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
  width: 100%;
  padding: var(--padding-main);
}

.search {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
  padding: 12px 16px;
  width: 506px;
  height: 48px;
  background: rgba(245, 244, 244, 0.4);
  border-radius: 8px;
}

.search__input {
  width: 100%;
  height: 100%;
  background-color: unset;
  border: none;
  color: var(--text-secondary);
}

.search__btn:focus,
.search__input:focus {
  outline: none;
}

.search__btn {
  width: 24px;
  height: 24px;
  background-image: url(./assets/icons/search.svg);
  background-repeat: no-repeat;
  background-position: center;
  background-size: contain;
  background-color: unset;
  border: none;
  cursor: pointer;
}

.main {
  display: flex;
  justify-content: space-between;
  padding: var(--padding-main);
}

.forecast {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding: 8px;
  align-items: center;
  text-align: center;
  width: 100%;
  color: var(--text-invert);
}

.forecast__city-info {
  width: 100%;
  display: flex;
  gap: 8px;
  flex-direction: column;
}

.forecast__city {
  font-size: 24px;
  font-weight: 700;
  line-height: 32px;
}

.search__input,
.forecast__city-info,
.forecast__date,
.forecast__time,
.forecast__conditions,
.forecast__feels {
  font-size: 20px;
  font-weight: 400;
  line-height: 24px;
}

.forecast__conditions {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 8px;
}

.forecast__icon {
  width: 24px;
  height: 24px;
}

.forecast__temperature {
  font-size: 112px;
  font-weight: bold;
  line-height: 112px;
}

.forecast__other-info {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 8px;
}

.card {
  width: 158px;
  height: 196px;
  background-color: var(--surface-primary);
  border-radius: 8px;
  display: flex;
  flex-direction: column;
  gap: 16px;
  padding: 16px;
  align-items: center;
  color: var(--text-primary);
}

.card__icon {
  width: 32px;
  height: 32px;
}

.humidity .card__icon {
  background-image: url("./assets/icons/32/details/humidity.svg");
}

.pressure .card__icon {
  background-image: url("./assets/icons/32/details/barometr.svg");
}

.visibility .card__icon {
  background-image: url("./assets/icons/32/details/visibility.svg");
}

.sunrise .card__icon {
  background-image: url("./assets/icons/32/details/sunrise.svg");
}

.sunset .card__icon {
  background-image: url("./assets/icons/32/details/sunset.svg");
}

.wind .card__icon {
  background-image: url("./assets/icons/32/details/direction/wse.svg");
}

.cards__list {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 16px;
  width: 506px;
  list-style-type: none;
}

.card__label {
  font-size: 16px;
  line-height: 20px;
  font-weight: 700;
}

.card__value {
  font-size: 32px;
  font-weight: 400;
  line-height: 32px;
}

.bar {
  width: 100%;
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.bar__progress {
  width: 100%;
  height: 8px;
  display: flex;
  background-color: var(--bar-bg);
  border-radius: 8px;
}

.pressure .bar__progress {
  background: radial-gradient(50% 9453.13% at 50% 50%,
      rgba(84, 84, 84, 0.4) 0%,
      rgba(138, 138, 138, 0.4) 45.12%,
      #dadada 100%,
      rgba(218, 218, 218, 0.4) 100%);
}

.bar__thumb {
  width: 8px;
  height: 8px;
  background-color: var(--thumb-bg);
  border-radius: 8px;
  position: relative;
}

.humidity .bar__thumb {
  left: 60%;
}

.pressure .bar__thumb {
  left: 73%;
}

.visibility .bar__thumb {
  left: 21%;
}

.bar__descr {
  display: flex;
  justify-content: space-between;
  color: var(--text-tertiary);
}

.bar__min,
.bar__max,
.bar__text {
  font-size: 12px;
  line-height: 16px;
  font-weight: 400;
  color: var(--text-tertiary);
}

.bar__max {
  text-align: right;
}

.bar__text {
  width: 100%;
  text-align: center;
}

.slider {
  height: 192px;
}

.footer {
  height: 84px;
}
</style>
