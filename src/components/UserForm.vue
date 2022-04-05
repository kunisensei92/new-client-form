<template>
	<div>
		<div class="form-wrapper">
			<div class="form-container grid">
				<div class="form-container-label">
					<h3>Данные пациента</h3>
				</div>
				<div class="form-container-input">
					<div class="input-block">
							<label for="second-name">Фамилия *</label>
							<input type="text" v-model="state.secondName" name="second-name" access="false" id="second-name" :class="{'is-invalid':v$.secondName.$error, 'is-valid':!v$.secondName.$invalid }">
							<div class="error-message" v-if="v$.secondName.$error"><span>Введите фамилию</span></div>
					</div>
					<div class="input-block">
							<label for="first-name">Имя *</label>
							<input type="text" v-model="state.firstName" name="first-name" access="false" id="first-name" :class="{'is-invalid':v$.firstName.$error, 'is-valid':!v$.firstName.$invalid }">
							<div class="error-message" v-if="v$.firstName.$error"><span>Введите имя</span></div>
					</div>
					<div class="input-block">
							<label for="patronymic">Отчество</label>
							<input type="text" v-model="state.patronymic" name="patronymic" access="false" id="patronymic">
					</div>
					<div class="input-block">
							<label for="gender">Пол</label>
							<div class="flex">
								<div class="radio-items">
									<input v-model="state.gender" name="gender" access="false" id="gender-0" value="male" type="radio" checked="checked">	
									<label for="gender-0">Мужской</label>
								</div>
								<div class="radio-items">									
									<input v-model="state.gender" name="gender" access="false" id="gender-1" value="female" type="radio">
									<label for="gender-1">Женский</label>
								</div>
							</div>
					</div>
					<div class="input-block">
							<label for="birth-date">Дата рождения *</label>
							<input type="date" v-model="state.birthDate" name="birth-date" access="false" id="birth-date" :class="{'is-invalid':v$.birthDate.$error, 'is-valid':!v$.birthDate.$invalid }">
							<div class="error-message" v-if="v$.birthDate.$error"><span>Введите дату рождения</span></div>
					</div>
					<div class="input-block">
							<label for="phone-number">Номер телефона * (пр. 79991234567)</label>
							<input type="tel" v-model="state.phoneNumber" name="phone-number" access="false" maxlength="11" id="phone-number" :class="{'is-invalid':v$.phoneNumber.$error, 'is-valid':!v$.phoneNumber.$invalid }">
							<div class="error-message" v-if="v$.phoneNumber.$error"><span>Введите номер телефона (11 цифр)</span></div>
					</div>
					<div class="input-block">
							<label for="client-group">Группа клиентов *</label>
							<select v-model="state.clientGroup" name="client-group[]" multiple="true" id="client-group" :class="{'is-invalid':v$.clientGroup.$error, 'is-valid':!v$.clientGroup.$invalid }">
									<option value="group-vip" id="client-group-0">VIP</option>
									<option value="group-problem" id="client-group-1">Проблемные</option>
									<option value="group-oms" id="client-group-2">ОМС</option>
							</select>
							<div class="error-message" v-if="v$.clientGroup.$error"><span>Выберите группу клиентов</span></div>
					</div>
					<div class="input-block">
							<label for="doctor">Лечащий врач</label>
							<select v-model="state.doctor" name="doctor" id="doctor" class="select-item">
								<option disabled value="">Выберите врача:</option>
								<option value="doctor-1" selected="true" id="doctor-0">Иванов</option>
								<option value="doctor-2" id="doctor-1">Захаров</option>
								<option value="doctor-3" id="doctor-2">Чернышева</option>
							</select>
					</div>
					<div class="input-block check-items">
						<input v-model="state.smsCheckbox" name="sms-checkbox" access="false" id="sms-checkbox" value="check" type="checkbox">
						<label for="sms-checkbox">Не отправлять СМС</label>
					</div>
				</div>
			</div>
			<div class="form-devider"><div class="border"></div></div>
			<div class="form-container grid">
				<div class="form-container-label">
					<h3>Адрес</h3>
				</div>
				<div class="form-container-input">
					<div class="input-block">
							<label for="country">Страна</label>
							<select v-model="state.country" name="country" id="country" class="select-item">
								<option disabled value="">Выберите страну:</option>
								<option value="country-1" selected="true" id="country-1">Россия</option>
							</select>
					</div>
					<div class="input-block">
							<label for="address-street" class="formbuilder-text-label">Улица</label>
							<input type="text" v-model="state.addressStreet" name="address-street" access="false" id="address-street">
					</div>
					<div class="input-block">
							<label for="address-home" class="formbuilder-text-label">Дом</label>
							<input type="text" v-model="state.addressHome" name="address-home" access="false" id="address-home">
					</div>
					<div class="input-block">
							<label for="city" class="formbuilder-text-label">Город *</label>
							<input type="text" v-model="state.city" name="city" access="false" id="city" :class="{'is-invalid':v$.city.$error, 'is-valid':!v$.city.$invalid }">
							<div class="error-message" v-if="v$.city.$error"><span>Введите город</span></div>
					</div>
					<div class="input-block">
							<label for="region" class="formbuilder-text-label">Область</label>
							<input type="text" v-model="state.region" name="region" access="false" id="region">
					</div>
					<div class="input-block">
							<label for="zip-code" class="formbuilder-text-label">Индекс</label>
							<input type="text" v-model="state.zipCode" name="zip-code" access="false" id="zip-code">
					</div>
				</div>
			</div>
			<div class="form-devider"><div class="border"></div></div>
			<div class="form-container grid">
				<div class="form-container-label">
					<h3>Паспорт</h3>
				</div>
				<div class="form-container-input">
					<div class="input-block">
							<label for="id-type">Тип документа *</label>
							<select v-model="state.idType" name="id-type" id="id-type" class="select-item" :class="{'is-invalid':v$.idType.$error, 'is-valid':!v$.idType.$invalid }">
									<option disabled value="">Выберите документ:</option>
									<option value="passport" selected="true" id="id-type-0">Паспорт</option>
									<option value="birth-certificate" id="id-type-1">Свидетельство о рождении</option>
									<option value="drivers-license" id="id-type-2">Вод. удостоверение</option>
							</select>
							<div class="error-message" v-if="v$.idType.$error"><span>Выберите тип документа</span></div>
					</div>
					<div class="input-block">
							<label for="passport-number-1">Серия</label>
							<input type="text" v-model="state.passportNumber1" name="passport-number-1" access="false" id="passport-number-1">
					</div>
					<div class="input-block">
							<label for="passport-number-2">Номер</label>
							<input type="text" v-model="state.passportNumber2" name="passport-number-2" access="false" id="passport-number-2">
					</div>
					<div class="input-block">
							<label for="issuer">Кем выдан</label>
							<input type="text" v-model="state.issuer" name="issuer" access="false" id="issuer">
					</div>
					<div class="input-block">
							<label for="issue-date">Дата выдачи *</label>
							<input type="date" v-model="state.issueDate" name="issue-date" access="false" id="issue-date" :class="{'is-invalid':v$.issueDate.$error, 'is-valid':!v$.issueDate.$invalid }">
							<div class="error-message" v-if="v$.issueDate.$error"><span>Введите дату выдачи</span></div>
					</div>
				</div>
			</div>
			<div class="button-submit col-span-6">
				<button type="submit" @click="submitForm">
					Отправить
				</button>
			</div>
		</div>
	</div>
</template>

<script>
	import useValidate from '@vuelidate/core'
	import { required, minLength} from '@vuelidate/validators'
	import { reactive, computed } from 'vue'

	export default {
		setup() {
			const state = reactive({
				firstName: '',
				secondName: '',
				patronymic: '',
				phoneNumber: '',
				gender: '',
				birthDate: '',
				clientGroup: '',
				doctor: '',
				smsCheckbox: '',
				country: '',
				addressStreet: '',
				addressHome: '',
				city: '',
				region: '',
				zipCode: '',
				idType: '',
				passportNumber1: '',
				passportNumber2: '',
				issuer: '',
				issueDate: ''
			})

			const rules = computed(() => {
				return {
					firstName: { required },
					secondName: { required },
					patronymic: '',
					phoneNumber: { required, minLength: minLength(11) },
					gender: '',
					birthDate: { required },
					clientGroup: { required },
					doctor: '',
					smsCheckbox: '',
					country: '',
					addressStreet: '',
					addressHome: '',
					city: { required },
					region: '',
					zipCode: '',
					idType: { required },
					passportNumber1: '',
					passportNumber2: '',
					issuer: '',
					issueDate:  { required }
				}
			})

			const v$ = useValidate(rules, state)

			return {
				state,
				v$,
			}
		},
		methods: {
			submitForm() {
				this.v$.$validate()
				if (!this.v$.$error) {
					alert('Новый клиент успешно создан.')
				}
			}
		}
	}
</script>

<style lang="scss" scoped>

</style>