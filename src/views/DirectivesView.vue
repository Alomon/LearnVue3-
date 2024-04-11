<template>
  <section class="m-4">

    <h3>Декларативная отрисовка</h3>
    <p>{{ message }}</p>

    <h3>Директива v-model</h3>
    <form class="form-control" action="#" method="POST">
      <input class="input-group m-2" v-model="login" type="text" name="login" value="" placeholder="Введите логин">
      <p class="m-2">Ваш логин: {{ login }}</p>
    </form>

    <h3>Директива v-if</h3>
    <div v-if="seen">
      <p>Этот блок виден, так как переменная seen - истина</p>
      <p>А второй блок не виден и убран из DOM-дерева</p>
    </div>
    <div v-if="!seen">
      <p>Второй блок</p>
    </div>

    <h3>Директива v-show</h3>
    <div v-show="seen">
      <p>Этот блок виден, так как переменная seen - истина</p>
      <p>А второй блок скрыт с помощью атрибута style="display: none;"</p>
    </div>
    <div v-show="!seen">
      <p>Второй блок</p>
    </div>

    <h3>Директива v-for (массив)</h3>
    <div>
      <p>Список фруктов:</p>
      <ol>
        <li v-for="fruit in fruits">{{ fruit }}</li>
      </ol>
    </div>

    <h3>Директива v-for (массив объектов)</h3>
    <div>
      <p>Список студентов:</p>
      <ul>
        <li v-for="student in students">
          ФИО: <b>{{ student.fio }}</b><br />
          Дата рождения: {{ student.birth }}<br />
          Пол: {{ student.sex }}
        </li>
      </ul>
    </div>

    <h3>Директива v-bind</h3>
    <div>
      <img :class="{img: active}" v-bind:src="bind_img" v-bind:alt="bind_value" :title="bind_value">
    </div>

    <h3>Директива v-on</h3>
    <div>
      <button v-on:click="active_true" class="btn btn-success">active: true</button>
      <button @click="active_false" class="btn btn-success m-1">active: false</button>
    </div>


  </section>
</template>

<script>
  export default {
    // Раздел с переменным
    data() {
      return {
        message: "Приветствую вас на курсе по изучению фреймворка Vue 3!",
        login: null,
        seen: true,
        fruits: ["Яблоко", "Апельсин", "Банан", "Груша"],
        students: [
          {
            fio: "Галацан Иван Павлович",
            birth: '22.05.2006',
            sex: "Мужской",
          },
          {
            fio: "Глазунов Иван Сергеевич",
            birth: '17.08.2006',
            sex: "Мужской",
          },
          {
            fio: "Огинский Иван Станиславович",
            birth: '29.03.2006',
            sex: "Мужской",
          },
        ],
        bind_img: "https://masterpiecer-images.s3.yandex.net/60c772735eb511eebfc2963c1ee369ba:upscaled",
        bind_value: 'Милый котик',
        active: true,
      }
    },
    // Методы
    methods: {
      active_true() {
        this.active = true;
      },
      active_false() {
        this.active = false;
      }
    }
  }
</script>

<style scoped>
  .img {
    width: 300px;
  }
</style>