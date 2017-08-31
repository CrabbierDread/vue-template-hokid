# Компонент модальных окон

  * `modals.vue` - Основной компонент. Управление окнами.
  * `popup.vue` - Попап. Компонент-контент для модального окна.

## Требования

Основной компонет должен подключается на уровне корня(`root`) приложения, в этом проэкте в `@/App.vue`.
Чтобы иметь доступ к методам модальных окон нужно сделать на него ссылку, через атирбут `ref`.


## Использование

Чтобы открыть модальное окно, нужно вызвать метод `open` и передать ему параметры,
описание будет ниже. Чтобы закрыть нужно вызвать метод `close`. Все просто.
Также компонент поддерживает события `open` и `close` - аналогиный сопособ открытия/закрытия.

```
// Пример доступа к модалкам из любого компонента
this.$root.$refs.modals.open({

  // Передаем компонент контента
  component: popup,

  // Указываем слой, на данный момент их 2-а
  layer: 2,

  // Передаем данные компоненту контента
  data: {
    type: 'alert',
    message: 'Ошибка'
  }
});
```

## Методы

 * `open(options: object)` - открыть модальное окно
 * `close(layer: number)` - закрыть модальное окно, в `layer` передается номер слоя
 * `closeAll()` - закрыть все слои модальных окон

## Опции, передаваемые в метод `open`.

 * `component` [обязательно] - компонет-контент, отвечает за контент модального окна
 * `layer` [обязательно] - слой на в котором будет открыто окно, всего их 2 на данный момент
 * `data` - кастомные данные, передаваемые в компонент-контент

## События компонента

 * `open` - прокси метода `open`
 * `opened` - модальное окно открыто, передает в колбэк `options`
 * `close` - прокси метода `close`
 * `closed` - модальное окно закрыто, передает в колбэк `options`