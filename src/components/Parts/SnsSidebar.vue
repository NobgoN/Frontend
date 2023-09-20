<script>
    /* コンポーネントをインポート */
    import SnsHome from './SnsHome.vue';
    import SnsSetting from './SnsSetting.vue';
    import SnsMembers from './SnsMembers.vue';
    import ModalWindow from './ModalWindow.vue';

    export default {
        props: {
        },

        /* 使用するコンポーネント */
        components: {
            SnsHome,
            SnsSetting,
            SnsMembers,
            ModalWindow,
        },
        data: () => ({
            /* 初期画面設定 */
            componentView: SnsHome,

            /* 画面切り替えの変数を定義 */
            current: 0,
            home: 0,
            members: 1,
            post: 2,
            settings: 3,

            /* モーダルウィンドウの切り替え変数 */
            ModalVisible: false,

            postNum: 0,

            
            
        }),
        methods: {
            /* モーダルウィンドウをcloseにしたときにフォントの大きさをもとに戻す */
            fontChange() {
                this.postNum = this.current
            },

            /* 画面切り替えの関数 */
            changeHome() {
                this.componentView = SnsHome
                this.current = this.home
                this.fontChange()
                
                
            },
            changeMembers() {
                this.componentView = SnsMembers
                this.current = this.members
                this.fontChange()
            },

            changePost() {
                this.current = this.post
                this.ModalVisible = true
                
                
            },
            changeSettings() {
                this.componentView = SnsSetting
                this.current = this.settings
                this.fontChange()
            },

            closeModal() {
                this.ModalVisible = false
                this.current = this.postNum
            }
            
        }
    }
</script>

<template>
    <!-- メイン -->
    <main id="main">
        <header id="header">
            <!-- 検索フォーム -->
            <form action="#" class="search-form">
                <label>
                    <input type="text" placeholder="キーワードを入力">
                </label>
                <button type="submit" aria-label="検索"></button>
            </form>
        </header>

        <!-- コンポーネント -->
        <component :is="componentView" />
        <ModalWindow :isVisible="ModalVisible" @close="closeModal"></ModalWindow>
    </main>

    <!-- サイドバー -->
    <aside id="sub">
        <a href="#"><img src="@/assets/images/SnsIcon.png" alt="SnsIcon" class="SnsIcon"></a>
        <!-- v-ifで文字の太さを変更 -->
        <div class="sub-button">
            <!-- homeボタン -->
            <button @click="changeHome">
                <img src="@/assets/images/home.png" alt="home" class="sub-images">
                <p v-if="current == home" style=" font-weight: bold; margin-left: 10px;">Home</p>
                <p v-else style="margin-left: 10px;">Home</p>
            </button>
            <!-- membersボタン -->
            <button @click="changeMembers">
                <img src="@/assets/images/member.png" alt="members" class="sub-images">
                <p v-if="current == members" style=" font-weight: bold; margin-left: 10px;">Members</p>
                <p v-else style="margin-left: 10px;">Members</p>
            </button>
            <!-- postボタン -->
            <button @click="changePost">
                <img src="@/assets/images/post.png" alt="post" class="sub-images" style="width: 20%;">
                <p v-if="current == post" style=" font-weight: bold; margin-left: 10px;">Post</p>
                <p v-else style="margin-left: 10px;">Post</p>
            </button>
            <!-- settingsボタン -->
            <button @click="changeSettings">
                <img src="@/assets/images/setting.png" alt="setting" class="sub-images">
                <p v-if="current == settings"  style=" font-weight: bold; margin-left: 10px;">Settings</p>
                <p v-else style="margin-left: 10px">Settings</p>
            </button> 
        </div>
    </aside>
</template>

<style scoped lang="scss">
/* ヘッダー */

#header {
    width: 100%;
    height: 50px;
    position: fixed;
    top: 0;
    background: #fff;
    border-bottom: 1px solid #ccc;
}

/* サイドバー */

#sub {
    border-right: 1px solid #ccc;
    top: 0;
    height: 100%;
    width: 330px;
    position: fixed;
    overflow: auto;
    background: #fff;
    padding: 20px;

    .SnsIcon {
        margin: 20px;
        width: 15%;
        cursor: pointer;
    }

    .sub-images {
        width: 15%;
        position: absolute;   
        top: 4;
        left: 15px;
    }
    /* home,memberなどのボタン */
    .sub-button {
        button {
            border: none;
            background: #fff;
            border-radius: 50px;
            justify-content: center;
            align-items: center;
            margin: 0 auto;
            width: fit-content;
            padding: 15px 50px;
            transition: 0.3s ease-in-out;
            font-size: 25px;
            position: relative;
            cursor: pointer;

            &:hover {
                background: #ccc;
                
            }
            &:after {
                content: '';
                width: 5px;
                height: 5px;
                transform: rotate(45deg) translateY(-50%);
                position: absolute;
                top: 50%;
                right: 20px;
                border-radius: 1px;
                transition: 0.3s ease-in-out;
            } 

            .font_bold {
                font-weight: bold;
            }
        }
    }
     /* ここまでhome,memberなどのボタン */

}

/* 検索フォーム */
.search-form {
    display: flex;
    width: 300px;
    height: 30px;
    align-items: center;
    overflow: hidden;
    border: 2px solid #2589d0;
    border-radius: 3px;
    position: absolute;
    top: 10px;
    left: 30%;

    input {
        width: 250px;
        height: 45px;
        padding: 5px 15px;
        border: none;
        box-sizing: border-box;
        font-size: 1em;
        outline: none;

        &:placeholder {
            color: #767d83;
        }
    }

    button {
        display: flex;
        justify-content: center;
        align-items: center;
        width: 50px;
        height: 45px;
        border: none;
        background-color: #2589d0;
        cursor: pointer;

        &:after {
            width: 20px;
            height: 20px;
            background-image: url('data:image/svg+xml;charset=utf8,%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20viewBox%3D%220%200%2024%2024%22%3E%20%3Cpath%20d%3D%22M23.7%2020.8%2019%2016.1c-.2-.2-.5-.3-.8-.3h-.8c1.3-1.7%202-3.7%202-6C19.5%204.4%2015.1%200%209.7%200S0%204.4%200%209.7s4.4%209.7%209.7%209.7c2.3%200%204.3-.8%206-2v.8c0%20.3.1.6.3.8l4.7%204.7c.4.4%201.2.4%201.6%200l1.3-1.3c.5-.5.5-1.2.1-1.6zm-14-5.1c-3.3%200-6-2.7-6-6s2.7-6%206-6%206%202.7%206%206-2.6%206-6%206z%22%20fill%3D%22%23fff%22%3E%3C%2Fpath%3E%20%3C%2Fsvg%3E');
            background-repeat: no-repeat;
            content: '';   
        }
    }
}
/* ここまで検索フォーム */

</style>