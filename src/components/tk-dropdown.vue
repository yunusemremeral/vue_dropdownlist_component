<template>
    <div class="dropdown-wrapper" :style="dropdownContainerStyle">
        <div class="tk-dropdown" @click="toggleDropdown">
            <div class="tk-dropdown-header">
                <i v-if="selectedOption" :class="'tk-' + selectedOption.icon" class="tk-dropdown-icon"></i>
                {{ selectedOption ? selectedOption.text : placeholder }}
                <span class="tk-dropdown-arrow" :class="{ 'tk-dropdown-arrow-rotate': isOpen }"></span>
            </div>
            <ul class="tk-dropdown-list" v-show="isOpen">
                <li v-for="(option, index) in options" :key="index" @click="selectOption(option)">
                    <i :class="'tk-' + option.icon" class="tk-dropdown-icon"></i>
                    <span class="tk-dropdown-text">{{ option.text }}</span>
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        options: {
            type: Array,
            required: true,
        },
        selectedOption: {
            type: Object,
            default: null,
        },
        placeholder: {
            type: String,
            default: "Select",
        },
        width: {
            type: String,
            default: "100%",
        },
    },
    data() {
        return {
            isOpen: false,
        };
    },
    computed: {
        dropdownContainerStyle() {
            return {
                width: this.width,
            };
        },
    },
    methods: {
        toggleDropdown() {
            this.isOpen = !this.isOpen;
        },
        selectOption(option) {
            this.$emit("update:selectedOption", option);
        },
    },
};
</script>

<style scoped>
.tk-dropdown {
    position: relative;
    cursor: pointer;
}
.tk-dropdown-header {
    display: flex;
    align-items: center;
    padding: 0.5rem;
    background-color: #f8f8f8;
    border: 1px solid #ccc;
    height: 1.5rem;
}
.tk-dropdown-arrow {
    border: solid #999;
    border-width: 0 2px 2px 0;
    padding: 0.19rem;
    transform: rotate(45deg);
    transition: transform 0.3s ease;
    position: absolute;
    right: 0.95rem;
}
.tk-dropdown-arrow-rotate {
    transform: rotate(225deg);
}
.tk-dropdown-list {
    position: absolute;
    top: 100%;
    left: 0;
    width: 100%;
    padding: 0;
    margin: 0;
    list-style: none;
    background-color: #fff;
    border: 1px solid #ccc;
    max-height: 200px;
    overflow-y: auto;
}
.tk-dropdown-list li {
    display: flex;
    align-items: center;
    padding: 0.5rem;
    cursor: pointer;
}

.tk-dropdown-list li:hover {
    background-color: #f0f0f0;
}
.tk-dropdown-icon {
    margin-right: 1rem;
    width: 1.625rem;
    height: 1.625rem;
    background-color: red;
    position: relative;
}
.small {
    height: 1.5rem;
}
.medium {
    height: 2rem;
}
.large {
    height: 3rem;
}.tk-dropdown-icon::after {
    content: "";
    position: absolute;
    border-right: 1px solid darkgray;
    right: -0.5rem;
    height: 100%;
}
</style>
