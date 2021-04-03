# vuetifyの学習

##　vuetifyのインストール
***
プロジェクトを始めるディレクトリ配下で下記のコマンドを実行する。
```
$ vue create vuetify-project
$ cd vuetify-project
$ npm run serve
```
完了するとローカルサーバのURLが表示されるので、ブラウザでアクセスする。  
確認が終えたらnpm run serveを一度停止し、vuetifyのインストールを行う。
```
$ vue add vuetify
```
プリセットの選択はデフォルトを選択。  
`npm run serve`を実行してブラウザで`http://localhost:8080/`にアクセスし、Vuetifyのログに変更された画面を確認。  
インストールは以上。

## vuetifyの準備
***
インストール直後のsrc/components/HelloWorld.vueファイルにVuefityインストール後に確認したブラウザに表示されている内容が記述されている。  
今回は学習のためv-appタグのみを残して初期化する。
```
<template>
  <v-app>

  </v-app>
</template>
```

今回はVuefityのドキュメントページと同様なレイアウトを作成。

## ナビゲーションバーの設定
***
ページトップにナビゲーションバーを設定するためにv-app-barタグ、サイトのタイトルを表示するためにv-toolbar-titleタグを追加。
```
<template>
  <v-app>
    <v-app-bar>
      <v-toolbar-title>Vuetify</v-toolbar-title>
    </v-app-bar>
  </v-app>
</template>
```
ナビゲーションバーに色をつけ流にはv-app-barタグに任意のカラーを設定する。
```
 <v-app-bar dark>
    <v-toolbar-title>Vuetify</v-toolbar-title>
 </v-app-bar>
```
ナビゲーションバーにどのような設定が行えるかはVuetifyのドキュメントで確認する。  
ドキュメントページにアクセスし、左側のナビゲーションバーからAPIを選択し、その中にあるv-app-barを選択。  
Propsに表示される項目を設定することができる。  
colorを使って色の設定を行うこともできる。色の設定にはred、greenなどの文字列、#033やrgba(255, 0, 0, 0.5)でも設定することができる。  
さらにprimary, secondary, error, infoでも色の設定を行うことが可能。これらの色設定はVuetifyの中で設定されており、設定変更をすることも可能。
```
<v-app-bar color="red"dark>
    <v-toolbar-title>Vuetify</v-toolbar-title>
</v-app-bar>
```
```
<v-app-bar color="info">
    <v-toolbar-title>Vuetify</v-toolbar-title>
</v-app-bar>
```

## フッターの設定
***
`v-footer`タグを利用。  
`v-app-bar`と同様に設定。
```
    <v-app-bar color="info" dark app>
      <v-toolbar-title>Vuetify</v-toolbar-title>
    </v-app-bar>
    <v-footer color="info" dark app>Vuetify</v-footer>
```

## サイドのナビゲーションメニューの設定
***
サイドのナビゲーションメニューの作成には`v-navigation-drawer`タグを使用。  
`v-app-bar`タグの上に追加。
```
<v-app>
    <v-navigation-drawer app>Navigation Lists</v-navigation-drawer>
    <v-app-bar color="info" dark app>
      <v-toolbar-title>Vuetify</v-toolbar-title>
    </v-app-bar>
    <v-footer color="info" dark app>Vuetify</v-footer>
  </v-app>
```

ナビゲーションメニューの表示・非表示が行えるようにハンバーガーメニューを追加。  
ハンバーガーメニューは`v-app-bar-nav-icon`タグとして準備されているのでこれを利用。
```
<v-navigation-drawer app>Navigation Lists</v-navigation-drawer>
    <v-app-bar color="info" dark app>
      <v-app-bar-nav-icon></v-app-bar-nav-icon>
      <v-toolbar-title>Vuetify</v-toolbar-title>
    </v-app-bar>
    <v-footer color="info" dark app>Vuetify</v-footer>
```

ハンバーガーメニューをクリックすることでナビゲーションメニューの表示・非表示を制御するために`v-app-bar-nav-icon`タグに`vue.js`の`click`イベントを設定。  
また、ナビゲーションメニュー(v-navigation-drawer)には`v-model`のデータプロパティ`drawer`を設定。
```
<template>
  <v-app>
    <v-navigation-drawer app v-model="drawer">Navigation Lists</v-navigation-drawer>
    <v-app-bar color="info" dark app>
      <v-app-bar-nav-icon @click="drawer=!drawer"></v-app-bar-nav-icon>
      <v-toolbar-title>Vuetify</v-toolbar-title>
    </v-app-bar>
    <v-footer color="info" dark app>Vuetify</v-footer>
  </v-app>
</template>

<script>
  export default {
    data() {
      return{
        drawer: null
      }
   }
  } 
</script>
```
ハンバーガーメニューのクリックによる動作はブラウザが表示されている幅によって変わる。  
ブラウザの幅を広げた時ナビゲーションメニューが上部から表示されているので、ナビゲーションバーの下に表示されるように`clipped`を利用する。
- `v-navigation-drawe`rに`clipped`を追加。  
- `v-app-bar`に`clipped-left`を追加。
```
<v-navigation-drawer app v-model="drawer" clipped>Navigation Lists</v-navigation-drawer>
    <v-app-bar color="info" dark app clipped-left>
      <v-app-bar-nav-icon @click="drawer=!drawer"></v-app-bar-nav-icon>
      <v-toolbar-title>Vuetify</v-toolbar-title>
    </v-app-bar>
```
# 各種コンポーネントの設定
***
## ボタンの設定
***
`v-app-bar`タグの中にボタンを追加。  
ボタンの作成は`v-button`タグを利用。
```
<v-app-bar color="info" dark app clipped-left>
      <v-app-bar-nav-icon @click="drawer=!drawer"></v-app-bar-nav-icon>
      <v-toolbar-title>Vuetify</v-toolbar-title>
      <v-btn>Button</v-btn>
    </v-app-bar>
```
2つのコンポーネントの間にスペースをとりたい場合はv-spacerタグを使う。
```
<v-app-bar color="info" dark app clipped-left>
      <v-app-bar-nav-icon @click="drawer=!drawer"></v-app-bar-nav-icon>
      <v-toolbar-title>Vuetify</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn>Button</v-btn>
    </v-app-bar>
```

## ドロップダウンメニューの設定
***
ボタンを押した時にドロップダウンメニューを表示される設定を行なう。  
ドロップダウンメニューの設定については`vuetifyのドキュメント`に記載されているコードを参考。  
Vuetifyのドキュメントの`UI Components`で`Menus`を選択。
```
<v-app-bar color="info" dark app clipped-left>
      <v-app-bar-nav-icon @click="drawer=!drawer"></v-app-bar-nav-icon>
      <v-toolbar-title>Vuetify</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-toolbar-items>
      <v-menu offset-y>
        <template v-slot:activator="{on}">
        <v-btn v-on="on" text elevation="24">Button</v-btn>
        </template>
        <v-list-item>
          <v-list-item-content>
            <v-list-item-title>hoge</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-menu>
      </v-toolbar-items>
    </v-app-bar>
```

`v-list-item`を追加することでドロップダウンメニューに含まれるメニューの項目を増やすことができる。

## リストの設定
***
`v-for`を利用し表示されるドロップダウンメニューの項目を設定する。`v-for`を利用するため新たにメニューの値の配列を持ったデータプロパティ`suppors`を追加。
```
<script>
  export default {
    data() {
      return{
        drawer: null,
        supports:[
          'HTML',
          'CSS',
          'JS',
          'Python',
          'Vue.js'
        ]
      }
   }
  } 
</script>
```
ドロップメニューの確認では、`v-list`タグの中に手動で入力していたが、`v-for`を利用して`vue.js`に設定したリストから項目を取り出しすよう書き換える。
```
<v-list>
  <v-list-item v-for="support in supports" :key="support">
    <v-list-item-content>
      <v-list-item-title>{{ support }}</v-list-item-title>
    </v-list-item-content>
  </v-list-item>
</v-list>
```

## アイコンの設定
***
Buttonの右側にmenu-downのアイコンを設定する。  
アイコンの設定は`v-icon`タグの中に`mdi-“アイコン名”`。
```
 <v-btn v-on="on" text elevation="24">Button<v-icon>mdi-menu-down</v-icon></v-btn>
```
`Button`をクリック後に表示される各ドロップダウンメニューにもアイコンの設定をする。
`supports`のデータプロパティを配列からオブジェクトに変更しアイコンの名前を設定。
```
supports:[
          {naame:'HTML',icon:'mdi-vuetify'},
          {name:'CSS',icon:'mdi-discord'},
          {name:'JS',icon:'mdi-bug'},
          {name:'Python',icon:'mdi-github'},
          {name:'Vue.js',icon:'mdi-stack-overflow'},
        ]
```
`v-for`も展開後に`name`と`icon`を設定できるように変更。
```
<v-list>
          <v-list-item v-for="support in supports" :key="support.name">
           <v-list-item-icon>
           <v-icon>{{ support.icon }}</v-icon>
           </v-list-item-icon> 
           <v-list-item-content>
             <v-list-item-title>{{ support.name }}</v-list-item-title>
           </v-list-item-content>
          </v-list-item>
        </v-list>
```
# ナビゲーションメニューの中身の設定
***
## タイトルの設定と色設定

`v-navigation-drawer`タグの中身を下記のように書き換える。その際、`v-list`タグを使用。  
タイトルタグの`v-list-item-title`に`class=”title”`を設定すると文字の大きさと太さが変わる。
```
<v-navigation-drawer app v-model="drawer" clipped>
      <v-container>
        <v-list-item>
          <v-list-item-content>
            <v-list-item-title class="title">
              Navigation lists
            </v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-divider></v-divider>
      </v-container>
    </v-navigation-drawer>
```
文字の色も変更。
```
<v-list-item-title class="title blue--text text--darken-2">
```
色の細かな設定は、Vuetifyのドキュメンテーションの`Styles&animationsのColors(Material Colors)`で確認。

## リストの設定
ドロップダウンメニューのリスト同様、ナビゲーションメニューの設定も`v-list`タグと`v-for`を使って設定。  
新たにデータプロパティnav_listsを追加します。
```
data() {
      return{
        drawer: null,
        supports:[
          {name:'HTML',icon:'mdi-vuetify'},
          {name:'CSS',icon:'mdi-discord'},
          {name:'JS',icon:'mdi-bug'},
          {name:'Python',icon:'mdi-github'},
          {name:'Vue.js',icon:'mdi-stack-overflow'},
        ],
        nav_lists:[
          {name: 'Getting Started',icon: 'mdi-vuetify'},
          {name: 'Customization',icon: 'mdi-cogs'},
          {name: 'Styles & animations',icon: 'mdi-palette'},
          {name: 'UI Components',icon: 'mdi-view-dashboard'},
          {name: 'Directives',icon: 'mdi-function'},
          {name: 'Preminum themes',icon: 'mdi-vuetify'},
        ]
      }
   }
```
```
<v-container>
        <v-list-item>
          <v-list-item-content>
            <v-list-item-title class="title blue--text text--darken-2">
              Navigation lists
            </v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-divider></v-divider>
        <v-list dense nav>
          <v-list-item v-for="nav_list in nav_lists" :key="nav_list.name">
            <v-list-item-icon>
              <v-icon>{{ nav_list.icon }}</v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title>{{ nav_list.name }}</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-container>
```
- `v-dividerタグ` : 横線
- `dense`  リストの高さ

