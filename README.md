# PROJECT-6. Задача кластеризации

Файл с исходными [данными](https://lms-cdn.skillfactory.ru/assets/courseware/v1/468638e49cb9e7d4b4dfdc296c1c778e/asset-v1:SkillFactory+DST-3.0+28FEB2021+type@asset+block/pj6_data.zip).

Для просмотра проекта с графиками в формате HTML можно воспользоваться [nbviewer]().  


## Содержание
[1. Описание](#описание)

[2. Задачи](#задачи)

[3. Краткая информация о данных](#информация-о-данных)

[4. Этапы](#этапы)

[5. Результат](#результат)



### Описание
Проект на платформе ***[Skillfactory](https://skillfactory.ru/)*** по закреплению знаний по темам:
 - EDA;
 - понижение размерности;
 - кластеризация.



### Задачи
Имеется набор данных, который содержит все транзакции, произошедшие в период с 01/12/2010 по 09/12/2011 для базирующейся в Великобритании компании, занимающейся онлайн-розничной торговлей. 
Компания в основном продает уникальные подарки на все случаи жизни. Многие клиенты компании являются оптовиками.

**Бизнес-задача:** произвести сегментацию существующих клиентов, проинтерпретировать эти сегменты и определить стратегию взаимодействия с ними.

**Техническая задача для специалиста в Data Science:** построить модель кластеризации клиентов на основе их покупательской способности, частоты заказов и срока давности последней покупки, определить профиль каждого из кластеров.

**Основные цели проекта:**
1. Произвести предобработку исходного набора данных о транзакциях.
2. Провести разведывательный анализ данных и выявить основные закономерности.
3. Сформировать набор данных о характеристиках каждого из уникальных клиентов.
4. Построить несколько моделей машинного обучения, решающих задачу кластеризации клиентов, определить количество кластеров и проинтерпретировать их.



### Информация о данных
ПДанные представляют собой таблицу в формате CSV, в каждой строке которой содержится информация об уникальной транзакции.

Признаки, описывающие каждую транзакцию:

* InvoiceNo — номер счёта-фактуры (уникальный номинальный шестизначный номер, присваиваемый каждой транзакции; буква "C" в начале кода указывает на отмену транзакции);
* StockCode — код товара (уникальное пятизначное целое число, присваиваемое каждому отдельному товару);
* Description — название товара;
* Quantity — количество каждого товара за транзакцию;
* InvoiceDate — дата и время выставления счёта/проведения транзакции;
* UnitPrice — цена за единицу товара в фунтах стерлингов;
* CustomerID — идентификатор клиента (уникальный пятизначный номер, однозначно присваиваемый каждому клиенту);
* Country — название страны, в которой проживает клиент.



### Этапы
1. Базовый анализ структуры данных.
2. Преобразование, очистка и анализ данных.
3. EDA.
4. Построение RFM таблиц.
5. Понижение размерности и кластеризация.
6. Визуализация и интепритация.



### Результат
 В рамках данного проекта были проведены следующие этапы:  
- первичный анализ и очистка данных;
- разведывательный анализ;
- формирование RFM таблицы, RFMQ таблицы и RFMQ таблицы, дополненной сгенерированными признакми;
- для всех таблиц проведено исследование по поиску оптимальной кластеризации, понижению размерности;
- визуализация и интерпретация кластеризации.


В целях исследования по поиску оптимальной кластеризации была написана функция, оптимизирующая с помощью библиотеки Optuna гиперпараметры пяти алгоритмов кластеризации: KMeans, GaussianMixture, AgglomerativeClustering, DBSCAN, HDBSCAN, оптимизация проводилась по метрики silhouette_score, также учитывались calinski_harabasz_score и davies_bouldin_score. 
В целях маркетинговой значимости количество кластеров было огрангичено от 3 до 10. Исследования данной функцией проводилась на сформированных таблицах с понижением размерности алгоритмами PCA и t-SNE, также для RFM таблицы выполнен подбор гиперпараметров без понижения размерности на стандартизированном и нормализованном датафрейме.  

В качестве эксперимента был разработан коэффициент интерпретации кластеризации, который численно может показать, насколько получившаяся кластеризация может быть хорошо интерпретируема. На основании данного коэффициента также был проведен поиск оптимальной кластеризацией.  