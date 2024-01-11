<template>
  <div class="flex">

    <div class="alf">

      <div class="">
        Словарь
      </div>

      <table>

        <tr>
          <th>Оригинал</th>
          <th>Шифр</th>
        </tr>

        <tr v-for="key in Object.keys(alf)">
          <td>{{ key }}</td>
          <td>{{ alf[key] }}</td>
        </tr>

      </table>
    </div>

    <div class="inp">
      <input autocomplete="off" type="text" name="form" data-error="Ошибка" placeholder="" class="input" v-model="valueInput">
      <p>{{ result }}</p>
      <p class="small">Если есть знак "?" значит символ неизвестен и ссылка не сработает</p>
      <p><a :href="link" target="_blank">Ссылка</a></p>
    </div>

  </div>
</template>

<script setup>
import {ref, watch} from 'vue';

const alf = {
  'а': 'х',
  'б': '?',
  'в': 'ч',
  'г': 'ц',
  'д': 'с',
  'е': 'р',
  'ё': '?',
  'ж': 'у',
  'з': '?',
  'и': 'э',
  'й': 'ь',
  'к': 'я',
  'л': 'ю',
  'м': 'щ',
  'н': 'ш',
  'о': 'ы',
  'п': '?',
  'р': 'е',
  'с': 'д',
  'т': '?',
  'у': 'ж',
  'ф': '?',
  'х': 'а',
  'ц': 'г',
  'ч': 'в',
  'ш': 'н',
  'щ': 'м',
  'ы': 'о',
  'ь': 'й',
  'э': 'и',
  'ю': 'л',
  'я': 'к',
  'А': 'Х',
  'Б': '?',
  'В': 'Ч',
  'Г': 'Ц',
  'Д': 'С',
  'Е': 'Р',
  'Ё': '?',
  'Ж': 'У',
  'З': '?',
  'И': 'Э',
  'Й': 'Ь',
  'К': 'Я',
  'Л': 'Ю',
  'М': 'Щ',
  'Н': 'Ш',
  'О': 'Ы',
  'П': '?',
  'Р': 'Е',
  'С': 'Д',
  'Т': '?',
  'У': 'Ж',
  'Ф': '?',
  'Х': 'А',
  'Ц': 'Г',
  'Ч': 'В',
  'Ш': 'Н',
  'Щ': 'М',
  'Ы': 'О',
  'Ь': 'Й',
  'Э': 'И',
  'Ю': 'Л',
  'Я': 'К',
  ' ': '5',
}

const valueInput = ref('');
const result = ref('');
const link = ref('');

watch(valueInput, () => {
  result.value = valueInput.value.trim().split('').map((item) => alf[item]).join('');
  link.value = `http://msk-lts-001.msk.evraz.com/kid/webserv.nsf/problemmonitor_main?openagent&req_fio=${result.value}0&it_spec=&otv_inic=&isp_inic=`
  console.log('result.value', result.value);
})

</script>

<style scoped>
TABLE {
  border-collapse: collapse;
  /* Убираем двойные линии между ячейками */
}

TD,
TH {
  padding: 3px;
  /* Поля вокруг содержимого таблицы */
  border: 1px solid black;
  /* Параметры рамки */
}

TH {
  background: #b0e0e6;
  /* Цвет фона */
}

.flex {
  display: flex;
  gap: 1rem;
}

.input {
  width: 300px;
}

.small {
  font-size: 0.7rem;
}
</style>