# Ленивая загрузка изображений

## Необходимые библиотеки
| Jquery | [jquery.min.js][PlDb] |
| ------ | ------ |
| **Lazyloading** | **[lazyloading.min.js][PlGh]** |

Подключаем 
```sh
<script src="jquery.js"></script>
<script src="jquery.lazyload.js"></script>
```

### После подключения файлов

Запоминаем размеры нужной нам картинки. 
Заходим [СЮДА](https://webdesign-master.ru/services/lazy/) и генерируем файл для превью.

Для картинок делаем такой html

```sh
<div class="b-lazy">
	<img src="data:image/gif;base64,R0lGODdhAQABAPAAAMPDwwAAACwAAAAAAQABAAACAkQBADs=" 
		 alt="some picture" 
		 data-src="original.jpg"
		 class="lazyload lazy__img">
</div>
```
**Важно:**
**src** -- сгенерированный код превью 
**data-src** -- реальное изображение

В главный *css-файл* вставляем такие стили: 
```sh
.b-lazy { 
    padding: 100% 0 0 0;
    position: relative  
}
.b-lazy .lazy__img { 
    position: absolute; 
    top: 0; 
    left: 0; 
    width: 100% 
}
```
И делаем инициализацию в js. 
Например, если все картинки имеют класс lazyload, то такая:
```sh
lazyload();
```
Иначе такая:
```sh
var images = document.querySelectorAll(".some-class");
lazyload(images);
```
Больше примеров и типов инициализации [здесь](https://appelsiini.net/projects/lazyload/)


### Зачем нужно превью?

Lazyloading работает так, что если изображение есть на нашем экране -- оно грузится, иначе нет. Изначально все *непрогрузившиеся* изображения будут иметь высоту 1px, что позволит влезть в область экрана ненужным картинкам и тоже их загрузить. Это является проблемой и для обхода  используют автогенерируемые gif превью на уровне base64. [Пример](https://webdesign-master.ru/demos/lazy-load/) 

### Зачем нужна обретка и css-классы? 

Если не задать их, то превью-изображения при некоторых стилях буду рендериться в минимальном соотношении в пикселях. Например, без должного задания css-стилей, превью 700-500 будет иметь соотношение 7:5 и в браузере будет отображено как 7px:5px. Эту проблему и решают обертка и классы.

   [PlDb]: <https://github.com/Vterebenin/lazyloading/blob/master/jquery.min.js>
   [PlGh]: <https://github.com/Vterebenin/lazyloading/blob/master/jquery.lazyload.min.js>

