# laravel9-vite-vue-laradock

### 環境需求
1.php8^   
2.composer   
3.npm
4.laradock

### 安裝流程
參考官網: https://laravel.com/docs/9.x/installation
個人是直接使用Composer安裝
```
composer global require laravel/installer
 
laravel new example-app
```

### 安裝 npm 相關套件
```
npm install
npm install vue@next vue-loader@next
npm i @vitejs/plugin-vue
```
### 修改 vite.config.js file
windows with laradock
```
import { defineConfig } from 'vite';
import laravel from 'laravel-vite-plugin';
import vue from '@vitejs/plugin-vue';

export default defineConfig({
    server: {
        host: '172.18.48.1' //本機與wsl的ip 可使用ipconfig查詢
    },
    plugins: [
        laravel({
            input: ['resources/css/app.css', 'resources/js/app.js'],
            refresh: true,
        }),
        vue()
    ],
});

```
linux with laradock
```
import { defineConfig } from 'vite';
import laravel from 'laravel-vite-plugin';
import vue from '@vitejs/plugin-vue';

export default defineConfig({
    server: {
        host: '0.0.0.0' //因linux本身與docker互相支持所以固定為0.0.0.0
    },
    plugins: [
        laravel({
            input: ['resources/css/app.css', 'resources/js/app.js'],
            refresh: true,
        }),
        vue()
    ],
});
```
