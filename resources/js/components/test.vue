<template>
    <div class="flex">
        <form @submit.prevent="setCookie()">
            <div class="enter-box">
                <label for="personName" class="enter-box__lable">ФИО</label>
                <input
                    type="text"
                    class="enter-box__input"
                    id="personName"
                    placeholder="введите данные"
                    v-model="values.personName"
                    @focus="writeField($event.target.id)"
                />
                <div class="enter-box__err"></div>
            </div>
            <div class="enter-box">
                <label for="dateOld" class="enter-box__label"
                    >Дата рождения</label
                >
                <input
                    type="date"
                    class="enter-box__input"
                    id="dateOld"
                    v-model="values.dateOld"
                    @focus="writeField($event.target.id)"
                />
                <div class="enter-box__err">
                    <p v-if="!values.dateOld && isVisible" class="enter-box__p">
                        обязательное поле для ввода
                    </p>
                </div>
            </div>
            <div class="enter-box">
                <label for="place" class="enter-box__label"
                    >Место рождения</label
                >
                <input
                    type="text"
                    class="enter-box__input"
                    id="place"
                    aria-describedby="emailHelp"
                    placeholder="введите данные"
                    v-model="values.place"
                    @focus="writeField($event.target.id)"
                />
                <div class="enter-box__err">
                    <p v-if="!values.place && isVisible" class="enter-box__p">
                        обязательное поле для ввода
                    </p>
                </div>
            </div>
            <div class="enter-box">
                <label for="pasportSer" class="enter-box__label"
                    >Номер серия паспорта</label
                >
                <input
                    type="text"
                    class="enter-box__input"
                    id="pasportSer"
                    aria-describedby="emailHelp"
                    placeholder="введите данные"
                    v-model="values.pasportSer"
                    @focus="writeField($event.target.id)"
                />
                <div class="enter-box__err">
                    <p
                        v-if="!values.pasportSer && isVisible"
                        class="enter-box__p"
                    >
                        обязательное поле для ввода
                    </p>
                </div>
            </div>
            <button type="submit" class="enter-box__btn">Отправить</button>
        </form>
    </div>
</template>

<script>
export default {
    name: "test",
    data() {
        return {
            values: {
                personName: "",
                dateOld: "",
                place: "",
                pasportSer: "",
            },
            isVisible: false,
        };
    },
    computed: {
        getValues() {
            return JSON.stringify(this.values);
        },
    },
    methods: {
        setCookie() {
            if (
                this.values.dateOld &&
                this.values.place &&
                this.values.pasportSer
            ) {
                this.isVisible = false;
                console.log(this.getValues);
                alert(`файл json: ${this.getValues}`);
                document.cookie = `data=${this.getValues}`;
                for (let key in this.values) {
                    this.values[key] = "";
                }
            } else {
                this.isVisible = true;
                return;
            }
        },
        cookie() {
            if (this.getCookie("data")) {
                return JSON.parse(this.getCookie("data"));
            } else {
                return false;
            }
        },
        writeField(name) {
            for (let key in this.values) {
                if (key === name) {
                    const cookie = this.cookie();
                    if (cookie) {
                        this.values[key] = cookie[name];
                    } else {
                        break;
                    }
                }
            }
        },
        getCookie(name) {
            var matches = document.cookie.match(
                new RegExp(
                    "(?:^|; )" +
                        name.replace(/([\.$?*|{}\(\)\[\]\\\/\+^])/g, "\\$1") +
                        "=([^;]*)"
                )
            );
            return matches ? decodeURIComponent(matches[1]) : undefined;
        },
    },
};
</script>

<style lang="scss" scoped>
* {
    margin: 0;
    padding: 0;
}
.flex {
    margin-top: 100px;
    display: flex;
    justify-content: center;
    align-items: center;
}
form {
    width: 300px;
    border: 1px solid black;
    padding: 10px;
    box-shadow: 0 0 30px 3px gray;
    background-color: rgba(235, 232, 232, 0.596);
}

.enter-box {
    margin-bottom: 10px;
    &__input {
        display: block;
        width: 100%;
    }
    &__btn {
        background-color: rgba(0, 98, 255, 0.863);
        border-radius: 5px;
    }
    &__btn:hover {
        box-shadow: 0 0 5px 1px gray;
    }
    &__p {
        color: red;
    }
    &__err {
        height: 20px;
    }
}
</style>