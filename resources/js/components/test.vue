<template>
    <div class="flex">
        <form @submit.prevent>
            <div class="enter-box">
                <label for="exampleInputEmail1" class="enter-box__lable"
                    >ФИО</label
                >
                <input
                    type="text"
                    class="enter-box__input"
                    id="exampleInputEmail1"
                    placeholder="введите данные"
                />
            </div>
            <div class="enter-box">
                <label for="exampleInputPassword1" class="enter-box__label"
                    >Дата рождения</label
                >
                <input
                    type="date"
                    class="enter-box__input"
                    id="exampleInputPassword1"
                />
            </div>
            <div class="enter-box">
                <label for="exampleInputEmail1" class="enter-box__label"
                    >Место рождения</label
                >
                <input
                    type="text"
                    class="enter-box__input"
                    id="exampleInputEmail1"
                    aria-describedby="emailHelp"
                    placeholder="введите данные"
                />
            </div>
            <div class="enter-box">
                <label for="exampleInputEmail1" class="enter-box__label"
                    >Номер серия паспорта</label
                >
                <input
                    type="text"
                    class="enter-box__input"
                    id="exampleInputEmail1"
                    aria-describedby="emailHelp"
                    placeholder="введите данные"
                />
            </div>
            <button type="submit" class="enter-box__btn">Отправить</button>
        </form>
    </div>
</template>

<script>
export default {
    name: "test",
};
</script>

<style lang="scss" scoped>
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
    &__input {
        display: block;
        width: 100%;
        margin-bottom: 10px;
    }
    &__btn {
        background-color: rgba(0, 98, 255, 0.863);
        border-radius: 5px;
    }
    &__btn:hover {
        box-shadow: 0 0 5px 1px gray;
    }
}
</style>