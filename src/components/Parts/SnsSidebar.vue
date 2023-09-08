<template>
    <header id="header"></header>

    <main id="main">
        <h2>MAIN BLOCK</h2>
        <router-link to="../second">次のページ</router-link>

    </main>

    <aside id="sub">
        <div class="profile">
            <h2>Profile</h2>
            <div class="profile-icon"></div>
        </div>
    </aside>
</template>

<style scoped lang="scss">
body {
    margin: 0;
    padding: 0;
}

#header {
    box-sizing: border-box;
    background: #ccc;
    height: 50px;
}

#main {
    box-sizing: border-box;
    margin-left: 320px;
    padding: 20px 40px;
}

#sub {
    box-sizing: border-box;
    top: 50px;
    height: 100%;
    width: 330px;
    position: fixed;
    overflow: auto;
    background: #eee;
    padding: 20px;
}

/* profile */

.profile {
    margin-left: 20%;
    display: flex;
    justify-content: space-between;
    h2 {
        margin-left: 50px;
    }

    .profile-icon {
        color: #000;
        position: absolute;
        margin-left: 3px;
        margin-top: 13px;
        width: 14px;
        height: 8px;
        border-left: solid 2px currentColor;
        border-right: solid 2px currentColor;
        border-top: solid 2px currentColor;
        border-bottom: solid 2px transparent;
        border-radius: 6px 6px 0 0;

        &:before {
            content: '';
            position: absolute;
            left: 2px;
            top: -10px;
            width: 8px;
            height: 8px;
            border-radius: 50%;
            border: solid 2px currentColor;
        }
    
    }
}

</style>