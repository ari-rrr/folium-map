# folium-map
# Состав команды: Татарников Артём, Куликова Арина, Донскова Алина

Владивосток — крупный город и порт на юге Дальнего Востока России. Административный центр Приморского края и Дальневосточного федерального округа. Крупный политический, культурный, научно-образовательный и экономический центр региона. 
По данным Росстата, население Владивостока на начало 2024 года составляет около 590 тыс. человек. Это второй по величине город в Дальневосточном федеральном округе после Хабаровска.
Административные границы города были выгружены из OSM, полигоны зданий скачаны с nextgis.com 

Для того, чтобы отделить здания ОКН от точечных объектов, был использован инструмент Select by location (выбирались только те точки, которые находятся внутри элементов полигонального слоя со зданиями). 
Самым сложным этапом в работе была выгрузка полигонов зданий, так как в OSM подгружены не все здания. Было испробовано несколько плагинов QGIS, но в итоге пришлось прибегнуть к помощи сторонних ресурсов. Сложным оказалась работа с проекциями, важно следить за их правильностью. Кроме того, сложным оказалось подобрать правильные цвета, так как для формата json и choropleth разные параметры, что вводило в заблуждение. 

По ссылке https://github.com/ari-rrr/folium-map/blob/main/README.md можно увидеть процесс создания карты, используемые инструменты и прочие детали работы. В работе создана веб-карта с помощью библиотеки folium.  

Основные методы:
1.Первичный анализ данных
2.Фильтрация и выбор столбцов
3.Интерактивное исследование GeoDataFrame
4.Работа с координатами и проекциями
5.Создание сетки (fishnet). Создание сетки квадратных ячеек из полигонов с использованием библиотеки shapely и добавление их в GeoDataFrame.
6.Пространственное объединение и агрегация данных
7.Визуализация с помощью Folium и Geopandas

Говоря про процесс создания, использовались библиотеки Pandas (для работы с табличными данными, предоставляющая структуры данных и операции для их манипуляций), GeoPandas (Расширение Pandas для работы с геоданными, предоставляющее поддержку геометрий и операции над ними) и Folium (библиотека для визуализации данных на интерактивных картах). Кроме того, использовалась библиотека shapely, предоставляющая инструменты для работы с геометрическими данными, а также для создания и манипуляции геометрическими объектами. Эти библиотеки позволяют эффективно обрабатывать, анализировать и визуализировать геоданные в Python, открывая широкие возможности для работы с пространственными данными различных форматов. 

Далее загружались данные из двух файлов в формате GeoJSON и использовалась библиотека GeoPandas (gpd). Происходит чтение файла с точками и полигонами ОКН с помощью функции gpd.read_file() из библиотеки GeoPandas, после чего вызывается метод .head(), который показывает первые несколько строк этого GeoDataFrame. После этого выводится список столбцов для объектов культурного наследия. Визуализация и исследование выбранных данных с использованием интерактивного метода explore().

Следующие шаги включают в себя: печать текущей системы координат данных и опционально перепроецирование данных в другую систему координат, определение границ данных, инициализация переменных для создания сетки, создание сетки квадратных ячеек путем итерации по координатам, создание GeoDataFrame для сетки и установка системы координат, добавление идентификаторов ячеек и интерактивное исследование данных, сохранение сетки в файл GeoPackage.

После чего происходит пространственное объединение точечных данных с сеткой и подсчет объектов в каждой ячейке сетки. Следующим шагом данные визуализируются и создается интерактивная карты Folium; добавляются границы Владивостока и районы с информацией о населении, слой сетки и полигонов ОКН с концентрацией объектов. С помощью плагинов Folium улучшается функционал карты.Также происходит добавление поиска по полигонам ОКН. 

После карта сохраняется.

Карта получилась наглядной и информативной. Теперь пользователи интернета могут наслаждаться изучением истории и культуры Владивостока в интерактивном формате. Проделанной работой гордимся, вышло достойно, получилось все.


https://ari-rrr.github.io/folium-map/
