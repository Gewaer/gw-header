<template>
    <dropdown :is-icon="false" class="app-switcher">
        <template slot="btn">
            <span class="app-mode">Apps</span>
            <i class="fas fa-th" />
        </template>
        <template slot="body">
            <a
                v-for="app in appsList"
                :key="`app-${app.id}`"
                :href="app.url"
                target="_blank"
                class="dropdown-item"
            >
                <span>{{ app.name }}</span>
            </a>
        </template>
    </dropdown>
</template>

<script>
export default {
    name: "GwAppSwitcher",
    props: {
        appsList: {
            type: Array,
            default() {
                return [];
            }
        }
    }
}
</script>

<style lang="scss">
.app-switcher {
    position: relative;
    display: flex;
    align-items: center;
    padding: 0 20px;
    color: var(--base-color);

    &::before {
        content: "";
        position: absolute;
        left: 0;
        top: 50%;
        transform: translateY(-50%);
        width: 1px;
        height: 40%;
        background-color: #4B4B4B;
    }

    .bp-dropdown__btn {
        height: 100%;

        .app-mode {
            font-size: 15px !important;
            font-family: 'Roboto';
            font-weight: bold;
            display: block;
            text-align: center;
            margin-right: 10px;
            margin-bottom: 2px;
        }
    }
}

@media(max-width: 992px) {
    .app-switcher {
        order: 1;
        margin-right: initial;
        padding: 0 10px;

        #app-grid {
            position: absolute;
            left: 0;
            margin: 0;
            top: 0;
            width: 100%;
            height: 100%;
            background: none;
        }
    }
}
</style>
