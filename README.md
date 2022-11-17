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
### 最後嘗試run看看
```
npm run dev
```
### 成功後去確認laravel是否有架起來
首先修改env檔設定   
參數請設定為自己環境的參數   
```
APP_URL=http://test.test
DB_CONNECTION=mysql
DB_HOST=mysql
DB_PORT=3306
DB_DATABASE=test
DB_USERNAME=root
DB_PASSWORD=root
```
之後看是要使用laradock的vhost啟動網站   
或是下指令啟動網站   
```
php artisan serve
```
---

### 如果是現成的案子拉下來後要注意的事項   
如果用docker 記得去容器裡面下指令   
```
npm install 
```
```
composer install 
or
composer install --ignore-platform-reqs
```
建立 .env 擋，並且設定   
建立 vite.config.js 擋，並且設定   
```
php artisan migrate
```
