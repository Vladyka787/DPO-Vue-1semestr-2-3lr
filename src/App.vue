<template>
  <div class="container-fluid overflow-hidden">
    <div class="row justify-content-evenly m-2">
      <!-- Левая часть экрана, место для ввода пользователем данных -->
      <div class="col">
        <div class="p-3 myBorder">
          <!-- Ввод пользователем ФИО -->
          <div class="input-group">
            <span class="input-group-text">ФИО</span>
            <!-- Ввод пользователем своего имени -->
            <input
                type="text" maxlength="25" aria-label="first name" placeholder="Имя" class="form-control"
                v-bind:value="first_name"
                @input="inputFirstName"
            >
            <!-- Ввод пользователем своей фамилии -->
            <input
                type="text" maxlength="25" aria-label="last name" placeholder="Фамилия" class="form-control"
                v-bind:value="last_name"
                @input="inputLastName"
            >
            <!-- Ввод пользователем своего отчества -->
            <input
                type="text" maxlength="25" aria-label="patronymic" placeholder="Отчество" class="form-control"
                v-bind:value="patronymic"
                @input="inputPatronymic"
            >
          </div>
          <div>
            <div
                v-if="error_first_name"
                class="alert alert-danger customAlert" role="alert">
              Имя пользователя не соответствует формату
            </div>
            <div
                v-if="error_last_name"
                class="alert alert-danger customAlert" role="alert">
              Фамилия пользователя не соответствует формату
            </div>
            <div
                v-if="error_patronymic"
                class="alert alert-danger customAlert" role="alert">
              Отчество пользователя не соответствует формату
            </div>
          </div>
          <!-- Ввод ссылки на фото -->
          <div class="input-group mt-3">
            <span class="input-group-text">Ссылка на фото</span>
            <input
                v-bind:value="photo"
                @input="inputPhoto"
                type="text" class="form-control" placeholder="URL" aria-label="URL"
            >
          </div>
          <!-- Ввод города -->
          <div class="input-group mt-3">
            <span class="input-group-text">Город</span>
            <input
                v-bind:value="city"
                @input="inputCity"
                type="text" class="form-control" placeholder="Город" aria-label="Город"
            >
          </div>
          <div
              v-if="error_city"
              class="alert alert-danger customAlert" role="alert">
            Город не соответствует формату
          </div>
          <!-- Ввод профессии -->
          <div class="input-group mt-3">
            <span class="input-group-text">Профессия</span>
            <input
                v-bind:value="profession"
                @input="inputProfession"
                type="text" class="form-control" placeholder="Профессия" aria-label="Профессия"
            >
          </div>
          <div
              v-if="error_profession"
              class="alert alert-danger customAlert" role="alert">
            Профессия не соответствует формату
          </div>
          <!-- Ввод телефона -->
          <div class="input-group mt-3">
            <span class="input-group-text">Телефон</span>
            <input
                v-bind:value="phone_number"
                @input="inputPhoneNumber"
                type="text" class="form-control" placeholder="Номер телефона" aria-label="Номер телефона"
            >
          </div>
          <div
              v-if="error_phone_number"
              class="alert alert-danger customAlert" role="alert">
            Номер не соответствует формату
          </div>
          <!-- Ввод email -->
          <div class="input-group mt-3">
            <span class="input-group-text">EMAIL</span>
            <input
                v-bind:value="email"
                @input="inputEmail"
                type="text" class="form-control" placeholder="example@mail.com" aria-label="email"
            >
          </div>
          <div
              v-if="error_email"
              class="alert alert-danger customAlert" role="alert">
            EMAIL не соответствует формату
          </div>
          <!-- Ввод даты рождения -->
          <div class="input-group mt-3">
            <span class="input-group-text">Дата рождения</span>
            <input
                v-bind:value="birthdate"
                @input="inputBirthdate"
                type="date" class="form-control" placeholder="YYYY-MM-DD" aria-label="birthdate"
            >
          </div>
          <div
              v-if="error_birthdate"
              class="alert alert-danger customAlert" role="alert">
            Поздравляю, вы слишком молоды.
          </div>
          <!-- Ввод образования -->
          <div class="input-group mt-3">
            <label class="input-group-text">Образование</label>
            <select
                class="form-select"
                v-bind:value="education"
                @input="inputEducation"
            >
              <option selected>Выбрать...</option>
              <option value="Среднее">Среднее</option>
              <option value="Среднее специальное">Среднее специальное</option>
              <option value="Неоконченное высшее">Неоконченное высшее</option>
              <option value="Высшее">Высшее</option>
            </select>
          </div>
          <div
              v-if="selected_education"
          >
            <!-- Ввод названия учебного заведения -->
            <div class="input-group mt-3">
              <span class="input-group-text">Учебное заведение</span>
              <input
                  v-bind:value="educational_institution"
                  @input="inputEducationalInstitution"
                  type="text" class="form-control" placeholder="Название учебного заведения"
                  aria-label="Учебное заведение"
              >
            </div>
            <div
                v-if="error_educational_institution"
                class="alert alert-danger customAlert" role="alert">
              Учебное заведение не соответствует формату
            </div>
            <!-- Ввод факультета -->
            <div class="input-group mt-3">
              <span class="input-group-text">Факультет</span>
              <input
                  v-bind:value="faculty"
                  @input="inputFaculty"
                  type="text" class="form-control" placeholder="Факультет" aria-label="Факультет"
              >
            </div>
            <div
                v-if="error_faculty"
                class="alert alert-danger customAlert" role="alert">
              Факультет не соответствует формату
            </div>
            <!-- Ввод специализации -->
            <div class="input-group mt-3">
              <span class="input-group-text">Специализация</span>
              <input
                  v-bind:value="specialization"
                  @input="inputSpecialization"
                  type="text" class="form-control" placeholder="Специализация" aria-label="Специализация"
              >
            </div>
            <div
                v-if="error_specialization"
                class="alert alert-danger customAlert" role="alert">
              Специализация не соответствует формату
            </div>
            <!-- Ввод года окончания -->
            <div class="input-group mt-3">
              <span class="input-group-text">Год окончания</span>
              <input
                  v-bind:value="year_of_ending"
                  @input="inputYearOfEnding"
                  type="text" class="form-control" placeholder="Год окончания" aria-label="Год окончания"
              >
            </div>
            <div
                v-if="error_year_of_ending"
                class="alert alert-danger customAlert" role="alert">
              Год не соответствует формату
            </div>
          </div>
          <!-- Ввод желаемой зарплаты -->
          <div class="input-group mt-3">
            <span class="input-group-text">Желаемая ЗП (₽)</span>
            <input
                v-bind:value="salary"
                @input="inputSalary"
                type="range" class="form-range" placeholder="ЗП" aria-label="ЗП" min="15000" max="250000" step="1000"
            >
          </div>
          <!-- Ввод ключевых навыков -->
          <div class="input-group mt-3">
            <span class="input-group-text">Ключевые навыки</span>
            <textarea
                v-bind:value="key_skills"
                @blur="inputKeySkills"
                class="form-control" aria-label="With textarea">
            </textarea>
          </div>
          <div
              v-if="error_key_skills"
              class="alert alert-danger customAlert" role="alert">
            Используйте буквы латинского алфавита. А так же пробелы и . , ! ? : ;
          </div>
          <!-- Ввод данных о себе -->
          <div class="input-group mt-3">
            <span class="input-group-text">О себе</span>
            <textarea
                v-bind:value="about_me"
                @blur="inputAboutMe"
                class="form-control" aria-label="With textarea">
            </textarea>
          </div>
          <div
              v-if="error_about_me"
              class="alert alert-danger customAlert" role="alert">
            Используйте буквы латинского алфавита. А так же пробелы и . , ! ? : ;
          </div>
        </div>
      </div>
      <!-- Правая часть экрана, отображения данных введенным пользователем -->
      <div class="col">
        <div class="p-3 myBorder" style="display: flex;">
          <div class="me-3" style="min-height: 300px; min-width: 250px; max-height: 300px; background-color: white;">
            <img :src="photo" class="img-fluid" style="display: flex; justify-content: center; color: #727A82;"
                 alt="Тут могло быть ваше фото">
          </div>
          <div>
            <div style="flex-wrap: wrap;">ФИО: {{ last_name }} {{ first_name }} {{ patronymic }}</div>
            <br>
            <div style="flex-wrap: wrap;">Город: {{ city }}</div>
            <br>
            <div style="flex-wrap: wrap;">Профессия: {{ profession }}</div>
            <br>
            <div>Номер телефона: {{ phone_number }}</div>
            <br>
            <div>EMAIL: {{ email }}</div>
            <br>
            <div>Дата рождения: {{ birthdate }}</div>
            <br>
            <div>Уровень образования: {{ education }}</div>
            <br>
            <div
                v-if="selected_education"
            >
              <div style="flex-wrap: wrap;">Учебное заведения: {{ educational_institution }}</div>
              <br>
              <div style="flex-wrap: wrap;">Факультет: {{ faculty }}</div>
              <br>
              <div style="flex-wrap: wrap;">Специализация: {{ specialization }}</div>
              <br>
              <div>Год обучения: {{ year_of_ending }}</div>
              <br>
            </div>
            <div>Желаемая зарплата: {{ salary }}₽</div>
            <br>
            <div style="flex-wrap: wrap;">Ключевые навыки: {{ key_skills }}</div>
            <br>
            <div style="flex-wrap: wrap;">О себе: {{ about_me }}</div>
            <br>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  data() {
    return {
      first_name: "",
      error_first_name: false,
      last_name: "",
      error_last_name: false,
      patronymic: "",
      error_patronymic: false,
      photo: "",
      city: "",
      error_city: false,
      profession: "",
      error_profession: false,
      phone_number: "",
      error_phone_number: false,
      email: "",
      error_email: false,
      birthdate: "",
      error_birthdate: false,
      salary: "",
      education: "Выбрать...",
      selected_education: false,
      educational_institution: "",
      error_educational_institution: false,
      faculty: "",
      error_faculty: false,
      specialization: "",
      error_specialization: false,
      year_of_ending: "",
      error_year_of_ending: false,
      key_skills: "",
      error_key_skills: false,
      about_me: "",
      error_about_me: false,
    }
  },
  methods: {
    // Функция для обработки данных при вводе имени
    inputFirstName(event) {
      this.first_name = event.target.value;

      let regexp = /^[А-Я][а-я]{2,24}/gmu;

      let result = this.first_name.match(regexp);

      if ((result !== null)) {
        if (result[0] === this.first_name) {
          this.error_first_name = false;
        } else {
          this.error_first_name = true;
        }
      } else {
        this.error_first_name = true;
      }
      if (this.first_name === "") {
        this.error_first_name = false;
      }
    },
    // Функция для обработки ввода фамилии
    inputLastName(event) {
      this.last_name = event.target.value;

      let regexp = /^[А-Я][а-я]{2,24}/gmu;

      let result = this.last_name.match(regexp);

      if ((result !== null)) {
        if (result[0] === this.last_name) {
          this.error_last_name = false;
        } else {
          this.error_last_name = true;
        }
      } else {
        this.error_last_name = true;
      }
      if (this.last_name === "") {
        this.error_last_name = false;
      }
    },
    // Функция для обработки ввода отчества
    inputPatronymic(event) {
      this.patronymic = event.target.value;

      let regexp = /^[А-Я][а-я]{2,24}/gmu;

      let result = this.patronymic.match(regexp);

      if ((result !== null)) {
        if (result[0] === this.patronymic) {
          this.error_patronymic = false;
        } else {
          this.error_patronymic = true;
        }
      } else {
        this.error_patronymic = true;
      }
      if (this.patronymic === "") {
        this.error_patronymic = false;
      }
    },
    // Функция для обработки ввода ссылки на фото
    inputPhoto(event) {
      this.photo = event.target.value;
    },
    // Функция для обработки ввода города
    inputCity(event) {
      this.city = event.target.value;

      let regexp = /^[А-Я][А-Яа-я ]{2,40}/gmu;

      let result = this.city.match(regexp);

      if ((result !== null)) {
        if (result[0] === this.city) {
          this.error_city = false;
        } else {
          this.error_city = true;
        }
      } else {
        this.error_city = true;
      }
      if (this.city === "") {
        this.error_city = false;
      }
    },
    // Функция для обработки ввода профессии
    inputProfession(event) {
      this.profession = event.target.value;

      let regexp = /^[А-Я][А-Яа-я ]{2,70}/gmu;

      let result = this.profession.match(regexp);

      if ((result !== null)) {
        if (result[0] === this.profession) {
          this.error_profession = false;
        } else {
          this.error_profession = true;
        }
      } else {
        this.error_profession = true;
      }
      if (this.profession === "") {
        this.error_profession = false;
      }
    },
    // Функция для обработки ввода номера телефона
    inputPhoneNumber(event) {
      this.phone_number = event.target.value;

      let regexp = /^((\+7|7|8)+([0-9]){10})$/gmu;

      let result = this.phone_number.match(regexp);

      if ((result !== null)) {
        if (result[0] === this.phone_number) {
          this.error_phone_number = false;
        } else {
          this.error_phone_number = true;
        }
      } else {
        this.error_phone_number = true;
      }
      if (this.phone_number === "") {
        this.error_phone_number = false;
      }
    },
    // Функция для обработки ввода email
    inputEmail(event) {
      this.email = event.target.value;

      let regexp = /^[-\w.]+@([A-z0-9][-A-z0-9]+\.)+[A-z]{2,4}$/gmu;

      let result = this.email.match(regexp);

      if ((result !== null)) {
        if (result[0] === this.email) {
          this.error_email = false;
        } else {
          this.error_email = true;
        }
      } else {
        this.error_email = true;
      }
      if (this.email === "") {
        this.error_email = false;
      }
    },
    // Функция для обработки ввода даты рождения
    inputBirthdate(event) {
      this.birthdate = event.target.value;

      let date_array = this.birthdate.split('-');

      let date_birthdate = new Date(date_array[0], date_array[1], date_array[2]);
      let date_now = new Date();

      date_birthdate.setFullYear(date_birthdate.getFullYear() + 18);

      if (date_birthdate.getTime() > date_now.getTime()) {
        this.error_birthdate = true;
      } else {
        this.error_birthdate = false;
      }
    },
    // Функция для обработки ввода желаемой зарплаты
    inputSalary(event) {
      this.salary = event.target.value;
    },
    // Функция для обработки ввода образования
    inputEducation(event) {
      this.education = event.target.value;

      if ((this.education === "Выбрать...") || (this.education === "Среднее")) {
        this.selected_education = false;
      } else {
        this.selected_education = true;
      }
    },
    // Функция для обработки ввода специализации
    inputSpecialization(event) {
      this.specialization = event.target.value;

      let regexp = /^[А-Я][А-Яа-я ]{2,70}/gmu;

      let result = this.specialization.match(regexp);

      if ((result !== null)) {
        if (result[0] === this.specialization) {
          this.error_specialization = false;
        } else {
          this.error_specialization = true;
        }
      } else {
        this.error_specialization = true;
      }
      if (this.specialization === "") {
        this.error_specialization = false;
      }
    },
    // Функция для обработки ввода учебного заведения
    inputEducationalInstitution(event) {
      this.educational_institution = event.target.value;

      let regexp = /^[А-Я][А-Яа-я ]{2,100}/gmu;

      let result = this.educational_institution.match(regexp);

      if ((result !== null)) {
        if (result[0] === this.educational_institution) {
          this.error_educational_institution = false;
        } else {
          this.error_educational_institution = true;
        }
      } else {
        this.error_educational_institution = true;
      }
      if (this.educational_institution === "") {
        this.error_educational_institution = false;
      }
    },
    // Функция для обработки ввода факультета
    inputFaculty(event) {
      this.faculty = event.target.value;

      let regexp = /^[А-Я][А-Яа-я ]{2,70}/gmu;

      let result = this.faculty.match(regexp);

      if ((result !== null)) {
        if (result[0] === this.faculty) {
          this.error_faculty = false;
        } else {
          this.error_faculty = true;
        }
      } else {
        this.error_faculty = true;
      }
      if (this.faculty === "") {
        this.error_faculty = false;
      }
    },
    // Функция для обработки ввода года окончания
    inputYearOfEnding(event) {
      this.year_of_ending = event.target.value;

      let regexp = /^[1|2][0-9]{3}/gmu;

      let result = this.year_of_ending.match(regexp);

      let date_now = new Date();

      if ((result !== null)) {
        if (result[0] === this.year_of_ending) {
          this.error_year_of_ending = false;
        } else {
          this.error_year_of_ending = true;
        }
      } else {
        this.error_year_of_ending = true;
      }
      if (this.year_of_ending === "") {
        this.error_year_of_ending = false;
      }

      if (this.year_of_ending > date_now.getFullYear()) {
        this.error_year_of_ending = true;
      }
    },
    // Функция для обработки ввода ключевых навыков
    inputKeySkills(event) {
      this.key_skills = event.target.value;

      let regexp = /^[а-яА-Я .,!?:;]{0,200}/gmu;

      let result = this.key_skills.match(regexp);

      if ((result !== null)) {
        if (result[0] === this.key_skills) {
          this.error_key_skills = false;
        } else {
          this.error_key_skills = true;
        }
      } else {
        this.error_key_skills = true;
      }
      if (this.key_skills === "") {
        this.error_key_skills = false;
      }
    },
    // Функция для обработки ввода ключевых навыков
    inputAboutMe(event) {
      this.about_me = event.target.value;

      let regexp = /^[а-яА-Я .,!?:;]{0,200}/gmu;

      let result = this.about_me.match(regexp);

      if ((result !== null)) {
        if (result[0] === this.about_me) {
          this.error_about_me = false;
        } else {
          this.error_about_me = true;
        }
      } else {
        this.error_about_me = true;
      }
      if (this.about_me === "") {
        this.error_about_me = false;
      }
    },
  }
}
</script>

<style>

div.myBorder {
  border-color: #DFDEDD;
  border-style: solid;
  border-width: 5px;
}

body {
  min-height: 100%;
  background-image: url("../src/assets/theme.jpeg");
  background-repeat: no-repeat;
  background-size: cover;
  background-position: top center;
}

.customAlert {
  padding: 0;
  width: fit-content;
  margin-bottom: unset;
}

.col {
  min-height: 500px;
}

</style>