<template>
    <div>
        <section>
            <transition-group name="list" tag="ul">
                <li v-for="(todoItem, index) in propsdata" :key="todoItem" class="shadow">
                    <i class="checkBtn fas fa-check" aria-hidden="true"></i>
                    {{ todoItem }}
                    <span class="removeBtn" type="button" @click="removeTodo(todoItem, index)">
                        <i class="far fa-trash-alt" aria-hidden="true"></i>
                    </span>
                </li>
            </transition-group>
        </section>
    </div>
</template>

<script>
export default {
    props: ['propsdata'],
    methods: {
        removeTodo(todoItem, index) {
            this.$emit('removeTodo', todoItem, index);
        }
    }
}
</script>

<style scoped>
    .list-enter-active, .list-leave-active {
        transition: all, 1s;
    }
    .list-enter, .list-leave-to {
        opacity: 0;
        transform: translateY(30px);
    }
    ul {
        padding-left: 0;
    }
    li {
        display: flex;
        min-height: 50px;
        height: 50px;
        line-height: 50px;
        margin: .5rem 0;
        padding: 0 .9rem;
        background: white;
        border-radius: 5px;
    }
    .checkBtn {
        line-height: 45px;
        color: #62acde;
        margin-right: 5px;
    }
    .removeBtn {
        margin-left: auto;
        color: #de4343;
    }
</style>