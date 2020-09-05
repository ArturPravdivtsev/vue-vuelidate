<template>
  <div id="app">
    <form @submit.prevent="submitHandler">
      <div class="input-field">
        <input
          id="lastname"
          v-model="lastname"
          type="text"
          :class="{ invalid: $v.lastname.$dirty && !$v.lastname.required }"
        >
        <label for="lastname">Фамилия</label>
        <span
          v-if="$v.lastname.$dirty && !$v.lastname.required"
          class="helper-text invalid"
        >
          Введите фамилию
        </span>
      </div>

      <div class="input-field">
        <input
          id="name"
          v-model="name"
          type="text"
          :class="{ invalid: $v.name.$dirty && !$v.name.required }"
        >
        <label for="name">Имя</label>
        <span
          v-if="$v.name.$dirty && !$v.name.required"
          class="helper-text invalid"
        >
          Введите имя
        </span>
      </div>

      <div class="input-field">
        <input
          id="patronymic"
          v-model="patronymic"
          type="text"
        >
        <label for="patronymic">Отчество</label>
      </div>

      <div class="input-field">
        <input
          id="datebirth"
          v-model="datebirth"
          type="date"
          :class="{ invalid: $v.datebirth.$dirty && !$v.datebirth.required }"
        >
        <label for="datebirth">Дата рождения</label>
        <span
          v-if="$v.datebirth.$dirty && !$v.datebirth.required"
          class="helper-text invalid"
        >
          Введите дату рождения
        </span>
      </div>

      <div class="input-field">
        <input
          id="phone"
          v-model="phone"
          type="text"
          placeholder="79999999999"
          :class="{ invalid: $v.phone.$error}"
        >
        <label for="phone">Номер телефона</label>
        <span
          v-if="$v.phone.$error"
          class="helper-text invalid"
        >
          Номер телефона должен быть в формате 79999999999
        </span>
      </div>

      <div class="input-field">
        <input
          id="gender"
          v-model="gender"
          type="text"
        >
        <label for="gender">Пол</label>
      </div>

      <div class="input-field">
        <select
          multiple
          v-model="group"
          :class="{ invalid: $v.group.$error}"
        >
          <option
            value="VIP"
          >
            VIP
          </option>
          <option
            value="Проблемные"
          >
            Проблемные
          </option>
          <option
            value="ОМС"
          >
            ОМС
          </option>
        </select>
        <label>Группа клиентов</label>
        <span
          v-if="$v.group.$error"
          class="helper-text invalid"
        >
          Выберите группу клиентов
        </span>
      </div>

      <div class="input-field">
        <select
          v-model="doctor"
        >
          <option
            value="Иванов"
          >
            Иванов
          </option>
          <option
            value="Захаров"
          >
            Захаров
          </option>
          <option
            value="Чернышева"
          >
            Чернышева
          </option>
        </select>
        <label>Лечащий врач</label>
      </div>

      <div class="input-field">
        <input
          id="sms"
          v-model="sms"
          type="checkbox"
          style="display: none;"
        >
        <label
          for="sms"
          class="check"
        >
          <svg width="18px" height="18px" viewBox="0 0 18 18">
            <path d="M1,9 L1,3.5 C1,2 2,1 3.5,1 L14.5,1 C16,1 17,2 17,3.5 L17,14.5 C17,16 16,17 14.5,17 L3.5,17 C2,17 1,16 1,14.5 L1,9 Z"></path>
            <polyline points="1 9 7 14 15 4"></polyline>
          </svg>
          Не отправлять СМС
        </label>
      </div>

      <div class="input-field">
        <input
          id="postcode"
          v-model="postcode"
          type="text"
        >
        <label for="postcode">Индекс</label>
      </div>

      <div class="input-field">
        <input
          id="country"
          v-model="country"
          type="text"
        >
        <label for="country">Страна</label>
      </div>

      <div class="input-field">
        <input
          id="region"
          v-model="region"
          type="text"
        >
        <label for="region">Область</label>
      </div>

      <div class="input-field">
        <input
          id="city"
          v-model="city"
          type="text"
          :class="{ invalid: $v.city.$error}"
        >
        <label for="city">Город</label>
        <span
          v-if="$v.city.$error"
          class="helper-text invalid"
        >
          Введите город
        </span>
      </div>

      <div class="input-field">
        <input
          id="street"
          v-model="street"
          type="text"
        >
        <label for="street">Улица</label>
      </div>

      <div class="input-field">
        <input
          id="building"
          v-model="building"
          type="text"
        >
        <label for="building">Дом</label>
      </div>

      <div class="input-field">
        <select
          v-model="document"
          :class="{ invalid: $v.document.$error}"
        >
          <option
            value="Паспорт"
          >
            Паспорт
          </option>
          <option
            value="Свидетельство о рождении"
          >
            Свидетельство о рождении
          </option>
          <option
            value="Вод. удостоверение"
          >
            Вод. удостоверение
          </option>
        </select>
        <label>Тип документа</label>
        <span
          v-if="$v.document.$error"
          class="helper-text invalid"
        >
          Выберите тип документа
        </span>
      </div>

      <div class="input-field">
        <input
          id="series"
          v-model="series"
          type="text"
        >
        <label for="series">Серия</label>
      </div>

      <div class="input-field">
        <input
          id="number"
          v-model="number"
          type="text"
        >
        <label for="number">Номер</label>
      </div>

      <div class="input-field">
        <input
          id="whom"
          v-model="whom"
          type="text"
        >
        <label for="whom">Кем выдан</label>
      </div>

      <div class="input-field">
        <input
          id="when"
          v-model="when"
          type="date"
          :class="{ invalid: $v.when.$dirty && !$v.when.required }"
        >
        <label for="when">Дата выдачи</label>
        <span
          v-if="$v.when.$dirty && !$v.when.required"
          class="helper-text invalid"
        >
          Введите дату выдачи
        </span>
      </div>

      <!-- <div class="input-field">
        <input
          id="limit"
          v-model.number="limit"
          type="number"
          :class="{ invalid: $v.limit.$dirty && !$v.limit.minValue }"
        >
        <label for="limit">Limit</label>
        <span
          v-if="$v.limit.$dirty && !$v.limit.minValue"
          class="helper-text invalid"
        >
          MinValue {{ this.$v.limit.params.minValue.min }}
        </span>
      </div> -->

      <button
        class="btn"
        type="submit"
      >
        Создать
      </button>
    </form>
    <div
      id="toast"
    >
      <div id="desc">Клиент успешно создан!</div>
    </div>
  </div>
</template>

<script>
import { required } from 'vuelidate/lib/validators'
export default {
  name: 'App',
  data: () => ({
    lastname: '',
    name: '',
    patronymic: '',
    datebirth: '',
    phone: '',
    gender: '',
    group: [],
    doctor: '',
    sms: false,
    postcode: '',
    country: '',
    region: '',
    city: '',
    street: '',
    building: '',
    document: '',
    series: '',
    number: '',
    whom: '',
    when: ''
  }),
  validations: {
    lastname: { required },
    name: { required },
    datebirth: { required },
    phone: { validFormat: val => /^((7)+[0-9]{10})*$/.test(val), required },
    group: { required },
    city: { required },
    document: { required },
    when: { required }
  },
  methods: {
    submitHandler () {
      if (this.$v.$invalid) {
        this.$v.$touch()
        return
      }
      this.$v.$reset()
      var x = document.getElementById("toast")
      x.className = "show";
      setTimeout(function(){ x.className = x.className.replace("show", ""); }, 5000);
    }
  }
}
</script>

<style lang="sass">
html
  line-height: 1.5
  font-family: -apple-system,BlinkMacSystemFont,Segoe UI,Roboto,Oxygen-Sans,Ubuntu,Cantarell,Helvetica Neue,sans-serif
  font-weight: 400
  color: rgba(0,0,0,.87)

::-webkit-datetime-edit
  color: #9e9e9e

form
  max-width: 500px
  margin: 0 auto

.input-field
  position: relative
  margin-top: 1rem
  margin-bottom: 1rem
  .helper-text
    position: relative
    min-height: 18px
    display: block
    font-size: 12px
    color: rgba(0,0,0,.54)
  select
    position: relative
    cursor: pointer
    background-color: transparent
    border: none
    border-bottom: 1px solid #9e9e9e
    outline: none
    height: 2rem
    line-height: 2rem
    width: 100%
    font-size: 16px
    margin: 0 0 8px 0
    padding: 0
    display: block
    -webkit-user-select: none
    -moz-user-select: none
    -ms-user-select: none
    user-select: none
    z-index: 1
    option
      color: #9E9E9E
      font-size: 14px
    &[multiple="multiple"]
      height: 5rem
      line-height: 5rem

button, input, select
  font-family: -apple-system,BlinkMacSystemFont,Segoe UI,Roboto,Oxygen-Sans,Ubuntu,Cantarell,Helvetica Neue,sans-serif
  font-size: 100%
  line-height: 1.15
  margin: 0
  overflow: visible

input, input[type=date], input[type=text]
  background-color: transparent
  border: none
  border-bottom: 1px solid #9e9e9e
  border-radius: 0
  outline: none
  height: 3rem
  width: 100%
  font-size: 16px
  margin: 0 0 8px 0
  padding: 0
  -webkit-box-shadow: none
  box-shadow: none
  -webkit-box-sizing: content-box
  box-sizing: content-box
  -webkit-transition: border .3s,-webkit-box-shadow .3s
  transition: border .3s,-webkit-box-shadow .3s
  transition: box-shadow .3s,border .3s
  transition: box-shadow .3s,border .3s,-webkit-box-shadow .3s

.input-field>label
  color: #9e9e9e
  font-size: 0.85rem
  cursor: text
  text-align: initial

.select-wrapper+label:after, input+label:after, input[type=date]+label:after, input[type=text]+label:after
  display: block
  content: ""
  position: absolute
  top: 100%
  left: 0
  opacity: 0
  -webkit-transition: opacity .2s ease-out,color .2s ease-out
  transition: opacity .2s ease-out,color .2s ease-out

[type=reset], [type=submit], button, html [type=button]
  -webkit-appearance: button

.btn
  -webkit-box-shadow: 0 2px 2px 0 rgba(0,0,0,.14), 0 3px 1px -2px rgba(0,0,0,.12), 0 1px 5px 0 rgba(0,0,0,.2)
  box-shadow: 0 2px 2px 0 rgba(0,0,0,.14), 0 3px 1px -2px rgba(0,0,0,.12), 0 1px 5px 0 rgba(0,0,0,.2)
  border: none
  border-radius: 2px
  display: inline-block
  height: 36px
  line-height: 36px
  padding: 0 16px
  text-transform: uppercase
  vertical-align: middle
  -webkit-tap-highlight-color: transparent
  font-size: 14px
  outline: 0
  text-decoration: none
  color: #fff
  background-color: #26a69a
  text-align: center
  letter-spacing: .5px
  -webkit-transition: background-color .2s ease-out
  transition: background-color .2s ease-out
  cursor: pointer

.helper-text.invalid
  color: #f44336

.select-wrapper.invalid>input.select-dropdown, .select-wrapper.invalid>input.select-dropdown:focus, input.invalid:not([type]), input.invalid:not([type]):focus, input.invalid[type=date]:not(.browser-default), input.invalid[type=date]:not(.browser-default):focus, input.invalid[type=datetime-local]:not(.browser-default), input.invalid[type=datetime-local]:not(.browser-default):focus, input.invalid[type=datetime]:not(.browser-default), input.invalid[type=datetime]:not(.browser-default):focus, input.invalid[type=email]:not(.browser-default), input.invalid[type=email]:not(.browser-default):focus, input.invalid[type=number]:not(.browser-default), input.invalid[type=number]:not(.browser-default):focus, input.invalid[type=password]:not(.browser-default), input.invalid[type=password]:not(.browser-default):focus, input.invalid[type=search]:not(.browser-default), input.invalid[type=search]:not(.browser-default):focus, input.invalid[type=tel]:not(.browser-default), input.invalid[type=tel]:not(.browser-default):focus, input.invalid[type=text]:not(.browser-default), input.invalid[type=text]:not(.browser-default):focus, input.invalid[type=time]:not(.browser-default), input.invalid[type=time]:not(.browser-default):focus, input.invalid[type=url]:not(.browser-default), input.invalid[type=url]:not(.browser-default):focus, textarea.materialize-textarea.invalid, textarea.materialize-textarea.invalid:focus
  border-bottom: 1px solid #f44336
  -webkit-box-shadow: 0 1px 0 0 #f44336
  box-shadow: 0 1px 0 0 #f44336

.check
  cursor: pointer
  position: relative
  margin: auto
  width: 18px
  height: 18px
  -webkit-tap-highlight-color: transparent
  transform: translate3d(0,0,0)
  &:before
    content: ""
    position: absolute
    top: -15px
    left: -15px
    width: 48px
    height: 48px
    border-radius: 50%
    background: rgba(#223254,.03)
    opacity: 0
    transition: opacity .2s ease
  svg
    position: relative
    z-index: 1
    fill: none
    stroke-linecap: round
    stroke-linejoin: round
    stroke: #C8CCD4
    stroke-width: 1.5
    transform: translate3d(0,0,0)
    transition: all .2s ease
    path
      stroke-dasharray: 60
      stroke-dashoffset: 0
    polyline 
      stroke-dasharray: 22
      stroke-dashoffset: 66
  &:hover 
    &:before
      opacity: 1
    svg
      stroke: #4285F4

#sms:checked + .check
  svg
    stroke: #4285F4
    path
      stroke-dashoffset: 60
      transition: all .3s linear
    polyline
      stroke-dashoffset: 42
      transition: all .2s linear
      transition-delay: .15s

#toast
  visibility: hidden
  max-width: 225px
  height: 50px
  margin: auto
  background-color: #333
  color: #fff
  text-align: center
  border-radius: 2px
  position: fixed
  z-index: 1
  left: 0
  right:0
  bottom: 30px
  font-size: 17px
  white-space: nowrap
  #desc
    color: #fff
    padding: 16px
    overflow: hidden
    white-space: nowrap
  &.show
    visibility: visible
    -webkit-animation: fadein 0.5s, expand 0.5s 0.5s,stay 3s 1s, shrink 0.5s 2s, fadeout 0.5s 2.5s
    animation: fadein 0.5s, expand 0.5s 0.5s,stay 3s 1s, shrink 0.5s 4s, fadeout 0.5s 4.5s

@-webkit-keyframes fadein
    from 
      bottom: 0
      opacity: 0
    to 
      bottom: 30px
      opacity: 1

@keyframes fadein
  from
    bottom: 0
    opacity: 0
  to
    bottom: 30px
    opacity: 1

@-webkit-keyframes expand
  from
    min-width: 50px
  to
    min-width: 350px

@keyframes expand
  from
    min-width: 50px
  to
    min-width: 350px

@-webkit-keyframes stay
  from
    min-width: 350px
  to
    min-width: 350px

@keyframes stay
  from
    min-width: 350px
  to
    min-width: 350px

@-webkit-keyframes shrink
  from
    min-width: 350px
  to
    min-width: 50px

@keyframes shrink 
  from
    min-width: 350px
  to
    min-width: 50px

@-webkit-keyframes fadeout
  from
    bottom: 30px
    opacity: 1
  to
    bottom: 60px
    opacity: 0

@keyframes fadeout
  from
    bottom: 30px
    opacity: 1
  to
    bottom: 60px
    opacity: 0
</style>
