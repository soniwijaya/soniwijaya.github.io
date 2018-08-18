---
layout: post
title: "Start React from Scratch - Fundamental React.js"
date: 2018-08-17 10:32:00
author: soniwijaya
categories: react
header-img: "images/blog/start-react-from-scratch/react.jpeg"
---

Tutor ini saya buat karena semata-mata ingin berbagi, untuk teman-teman saya yg ingin memulai karirnya di bidang *Front-End Developer*. **React** merupakan FrameWork Terbaik Saat ini Menurut Saya.

Jika ingin memulai belajar FrameWork Terpopuler saat ini yaitu **React** maka *Javascript* adalah base code yang paling dasar dan wajib harus kamu ketahui. Dasar javascript yang seperti apa sih? hmm.. sebelum masuk ke *Javascript* adakah yang tau apa itu Ecmascript? **Javascript === Ecmascript.**

Di era teknologi saat ini, perkembangan teknologi itu sangat cepat berubah dari waktu ke waktu. maka dari itu kita yang harus segera untuk bisa beradaptasi. jadi seperti yang saya katakan tadi saat ini EcmaScript yg === *Javascript* sudah berada di Versi 8 (ES8). sepertinya sudah mulai ketinggalan kalau belajar ES6. kemudian apa saja perubahannya dari versi - versi tersebut?

* dari Segi Syntax dan fitur - fiturnya
* Mengenai Class, Object, Module, serta cara memanipulasinya

Jika kita sudah mulai terbiasa dengan penulisan gaya syntax ES6. kita memerlukan beberapa tools yg cukup canggih untuk mengkonversi Versi ES6 untuk turun ke versi ES5. Kenapa kita perlu melakukan hal tersebut?

Seupdate - updatenya teknologi pasti ada aja, yg perlu waktu untuk menyesuaikannya. Yah intinya beberapa browser belum kompatibel dengan gaya penulisan ES6. maka untuk menyeimbangkannya kita perlu

```
Babel - is a *Javascript* compiler https://babeljs.io/
Webpack - buddle your styles, assets, scripts. https://webpack.js.org/
```

![Babel]({{ "/images/blog/start-react-from-scratch/babel.png" | absolute_url }})

Sekilas mengenai pemahamannya. Untuk menjalankan Javascript ini, kita memerlukan yang namanya sebuah **Enviroment** agar Javascript ini bisa dijalankan *compiler*. Enviroment tersebut adalah **Node.js**. cara menginstalnya tidaklah susah saya mengunakan **PACKAGE MANAGER** dokumentasi lengkapnya ada disini - https://nodejs.org/en/download/package-manager/ kebetulan saya memilih memakai Node.js Versi 8 dengan base yg berjalan di **OS Ubuntu 16.04 LTS**.

Pada saat sudah selesai menginstal Node.js. Biasanya perlu dipastikan apakah sudah terinstal dengan baik atau belum. bisa dijalankan pada terminal dengan menjalankan kode dibawah ini.
```
node -v
npm -v
```
**NPM itu apa? NPM itu - package manager for Javascript** - https://www.npmjs.com/

Sekarang adalah tahap yg paling ditunggu karena akan dimulai pembahasan tema ini **React**, **INI BARU MULAI**. Kemudian yang tadi itu apa? itu baru proses yang dijalankan dibalik **React**, dan sebenarnya masih ada lagi. Namun jika dijelaskan secara detail akan memerlukan waktu yang cukup panjang, jadi saya potong saja sampai disini. Oke sekarang kita buat folder atau **directory (sebagai wadah untuk React)**.

```
mkdir react-from-scratch
cd react-from-scratch
npm init
```

Dibawah ini adalah tampilan dari **"npm init"**. ditampilkan beberapa pertanyaan mengenai bundle atau asset yang perlu dibuat dalam sebuah directory. silakan diisi seperti dibawah ini. setelah selesai maka akan meng - generate suatu file bernama **package.json**.

![NPM]({{ "/images/blog/start-react-from-scratch/npminit.png" | absolute_url }})

Kemudian buatlah sebuah file index.html sesuai standard **W3C Candidate Recommendation: HTML 5.1**, standard apa lagi ini? untuk lebih lengkapnya kunjungi saja link dibawah tersebut. Kegunaan file index.html nantinya untuk meng-render hasil component dari **React**.  
```
https://www.w3.org/TR/2017/REC-html51-20171003/introduction.html#introduction 
```

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie-edge">
    <title>Simple React</title>
</head>
<body>
    <div id="app"></div>

    <script src="dist/app.bundle.js"></script>
</body>
</html>
```

Move to the next step, lanjutkan dengan menginstal **WEBPACK**. Untuk instalasinya kita perlu menggunakan NPM. Contohnya seperti di bawah nih.

```
npm i webpack webpack-cli webpack-dev-server
```

Tunggu 15 menit, itu kalau koneksinya kenceng (Cek WI-FE nya). Nah kalau sudah kita harus membuat konfigurasi webpack dengan nama file webpack.config.js. Tujuan file ini untuk menkonversi syntax ES6 yang ada di src/main.js ke dalam bentuk ES5 (Old Javascript).

Untuk menjalakan webpack yg sudah kita buat barusan, buka package.json dan edit dibagian script seperti ini.

```
"scripts": {
    "start": "webpack-dev-server --config ./webpack.config.js --mode development"
},
```

isi dari webpack.config.js
```
module.exports = {
    entry: [
        './src/main.js'
    ],
    output: {
        path: __dirname + '/dist',
        publicPath: '/dist',
        filename: 'app.bundle.js'
    },
    devServer: {
        inline: true,
        port: 8080,
        contentBase: './'
    }
}
```

Lanjut... kita coba dulu testing webpacknya.. dan liat keajaiban yg terjadi.. kita buat file dengan nama main.js. kita letakkan di folder src/main.js. dan isi console.log("It Works Guys").
dan **"npm start"**.

![Webpack Testing]({{ "/images/blog/start-react-from-scratch/done.png" | absolute_url }})
 
Kemudian coba ubah lagi kata-kata yg ada di console.log menjadi "Apa bisa berubah *Automatic*" ?. Ternyata belum bisa ya teman-teman, kalau begitu repot ya mesti dijalankan berkali-kali. Apa ada cara praktisnya? pasti ada!!. Makanya kita perlu **menginstal babel, preset react, dan set-up babel loader di webpack config**

**NOTE** kegunaan babel loader untuk mereload file app.bundle.js yg kita buat tadi. supaya direload *automatic* gitu.
```
npm install babel-core babel-loader babel-preset-env
npm install babel-preset-react babel-preset-stage-2
```

```
resolve: {
        extensions: ['*', '.js', '.jsx']
    },
    module: {
        rules: [
            {
                test: /\.(js|jsx)$/,
                exclude: /node_modules/,
                use: ['babel-loader']
            }
        ]
    }
```

Buat file .babelrc dan **instal "npm install react react-dom"**
```
{
    "presets": [
        "env",
        "react",
        "stage-2"
    ]
}
```
Akhirnya sudah install **React** juga, saatnya kita mencoba untuk rendering dengan **React**, Buat *hello world* dulu, haha. Tinggal edit file main.js menjadi seperti ini.

```
import React from 'react' // ini penulisan gaya ES6
import ReactDOM from 'react-dom' // ini ES6

ReactDOM.render(
    <h1>Hello World!</h1>
    document.getElementById('app')
)
```

![Hello World]({{ "/images/blog/start-react-from-scratch/wowreact.png" | absolute_url }})

Permainannya tidak usai sampai disana, sekarang kita mainkan dengan *component*, buat dulu *component*nya. Posisinya letakkan didirectory "/src/components" dengan nama file Hello.jsx.
```
import React from 'react'

export default class Hello extends React.Component {
    constructor (){
        super()
        this.state = {
            react: "Welcome React"
        }
    }

    render(){
        return (
            <div>
                <h1>{ this.state.react }</h1>
                <h2>Mudahnya belajar kalau dari scratch</h2>
            </div>
        )
    }
}
```

**Dan jangan ketinggalan di main.js nya juga diubah ya!!** karena rendernya dari *component Hello.jsx*
```
import Hello from './components/hello'

ReactDOM.render(
    <Hello />,
    document.getElementById('app')
)
```

![JSX Component]({{ "/images/blog/start-react-from-scratch/selesai.png" | absolute_url }})

Oke sampai disini dulu tutorial Reactnya.. Semoga tutor ini dapat membantu anda memahami konsep fundamentalnya.

**Kalau ingin bertanya silakan tinggalkan komentar dibawah yah..**

**Jika kalian tertarik dengan pembelajaran React ini, dan ingin lebih Advanced, Tinggalkan Judul yg diingin dibahas** 

**"Stay Curiosity, Tetap belajar dan selalu BERKARYA".**


