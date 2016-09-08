# Yandex maps

Поле выводит Яндекс-карту с возможностью отметки на ней объектов. Объект возможно добавить
двойным кликом по карте. От бекенда ожидаются координаты в виде строки, например: "37.620393,55.765575".

```json
{
    "name": "coordinates",
    "label": "Карта",
    "type": "yandex-maps",
    "hint": "Это поле карты",
    "required": true,
    "expandable": true,
    "multiple": true,
    "filterable": true,
    "readonly": true,
    "list": true,
    "multiname": "new_value",
    "mapHeight": 400,
    "mapWidth": 400,
    "mapCenter": [37.620393,55.765575],
    "mapZoom": 5,
    "defaultValue" : "37.617313,55.756039"
}
```

## Параметры

* **name**: имя поля на бекенде.
* **label**: название поля (выводится в интерфейсе редактора).
* **type**: тип поля.
* **hint**: текстовая информационная подсказка, выводимая слева от заголовка поля.
* **required**: является ли поле обязательным для заполнения.
* **expandable**: требуется ли дополнительно запрашивать это поле у бекенда. Если установлено, то запрос на получение
сущности будет выполнен в формате:
```
/rest/v1/news?expand=coordinates
```
* **multiple**: параметр отвечает за указание возможности поля принимать множественные значения.
* **filterable**: параметр отвечает за добавление поля в форму фильтрации. Данный параметр можно указывать только у полей
первого уровня. Для полей вложенных в связанные сущности ( которые находятся внутри полей с типом array) фильтры не
будут созданы. По умолчанию добавляет все поля, за исключением тех у которых данный параметр установлен в false;
* **readonly**: параметр указывает на запрет редактирования поля.
* **list**: нужно ли отображать поле в списке записей. Не действует для вложенных в массивы полей. Для того, что бы
таблица не была пустой, требуется указать данный параметр со значением true хотя бы для одного поля.
* **multiname**: ключ, который будет использован для создания массива в запросе к бекенду в том случае, если поле
работает в множественном режиме. Если ключ не установлен, то на бекенд отправится массив вида
`['value1', 'value2', 'value3']`. Если ключ установлен, например: `multiname:"value"`, то на бекенд отправится
массив вида `[["value"=>"value1"], ["value"=>"value2"], ["value"=>"value3"]`.
* **requiredField**: параметр делает поле неактивным при пустом значении другого поля, указанного в данном параметре.

* **mapHeight**: отвечает за высоту контейнера, содержащего карту. Значение по умолчанию — 400 пикс.
* **mapWidth**: отвечает за ширину контейнера, содержащего карту. Значение по умолчанию — 400 пикс.
* **mapCenter**: отвечает за центровку карты. Значение по умолчанию — [37.620393,55.765575] (координаты центра Москвы).
* **mapZoom**: отвечает за масштаб карты. Допустимые значения от 0 до 23 включительно. 0 — самый мелкий (вся земля). Значение по умолчанию — 5.
* **defaultValue** : значение поля по-умолчанию(первое число широта, второе - долгота).