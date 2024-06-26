# Прогнозирование стоимости жилья в жилом массиве

## Описание проекта
Данный проект посвящен разработке модели прогнозирования стоимости квартир в жилом массиве. Сервис по продаже квартир начал разработку этой модели для определения медианной стоимости жилья на рынке.

## Навыки и инструменты
- Pandas
- Python
- Spark

## Задачи проекта
1. Провести анализ данных о жилом массиве.
2. Подготовить данные для построения модели.
3. Разработать модель прогнозирования стоимости квартиры.
4. Определить медианную стоимость квартиры на основе построенной модели.

## Вывод
1. Инициализирована локальная Spark-сессия.
2. Прочитано содержимое файла /datasets/housing.csv.
3. Выведены типы данных колонок датасета и проведен обзор данных:
    1. Датасет состоит из 10 столбцов и 20 640 строк;
    2. В столбце `total_bedrooms` обнаружено 207 пропущенных значений, которые необходимо обработать;
    3. Столбец `ocean_proximity` категориальный и имеет тип данных string, остальные количественные и тип double;
    4. Целевой признак - `median_house_value`.
4. Выполнена предобработка данных:
    1. Данные исследованы на наличие пропусков и заполнены средним занчением.
    2. Преобразована колонка с категориальным значенем `ocean_proximity` техникой One hot encoding.
5.  Обучены модели линейной регрессии на различных наборах данных показало следующие результаты:
    1. модель, обученная на всех признаках:
        * R2 - 0.64
        * MAE - 50089.95
        * RMSE - 70022.78
    
    2. модель, обученная только на числовых признаках
        * R2 - 0.63
        * MAE - 50842.87
        * RMSE - 71026.19

Значения метрик (коэффициент детерминации R2, средняя абсолютная ошибка MAE и корень среднего квадрата ошибок RMSE) получились лучше у модели, обученной на всех признаках - категориальных и числовых.
