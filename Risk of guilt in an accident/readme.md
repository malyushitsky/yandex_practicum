# Краткое описание проекта

Нужно создать систему, которая могла бы оценить риск виновности в ДТП. Под риском понимается вероятность оказаться виновным в ДТП с любым повреждением транспортного средства. Как только водитель забронировал автомобиль, сел за руль и выбрал маршрут, система должна оценить уровень риска. Если уровень риска высок, водитель увидит предупреждение и рекомендации по маршруту.

# Задачи проекта

1. Построить различные ML модели с перебором гиперпараметров
2. Провести анализ важности факторов на основе лучшей модели
3. Сформировать рекомендации по улучшению системы

# Используемые модели в проекте:

1. Модель логистической регрессии
2. Модель случайного леса
3. Бустинговая модель Catboost

# Метрики качества:
- Accuracy
- F1
- Roc-Auc

# Сравнительная таблица качества моделей на основе кросс-валидации

|                      Метрики качества                   |  Модель логистической регрессии |   Модель случайного леса  | Модель бустинга |
| :-----------------------------------------------:|:--------:| :-----:| :-----: |
| F1               | 0.54     | 0.57  | 0.58  |
| Accuracy         | 0.61     | 0.63  | 0.63  |
| Roc-Auc          | 0.65     | 0.67  | 0.68  |

# Выводы по проекту: 
- Лучшей моделью была выявлена **бустинговая модель Catboost**. Получившиеся метрики качества модели:
1. F1 - 0.57
2. Accuracy - 0.63
3. Roc-Auc - 0.68
4. Recall - 0.49
5. Precision - 0.69

- Наиболее важными факторами, на основе модели были выделены `трезвость участника` (в нетрезвом виде гораздо больше было виновных чем невиновных) и `сумма страховки`. Чем она выше, тем ниже вероятность виновности водителя, поскольку сумма страховки зависит от различных факторов, таких как стаж вождения, возраст водителя, наличие/отсутствие аварий за год и др., то можно предположить, что водители с высокой суммой страховки стараются быть более аккуратными на дороге. Из этого вытекает вывод о правильно выявленной закономерности со стороны модели.

- Конечно в данном виде модель нельзя назвать удовлетворительной, с задачей классификации риска для водителя стать виновник дтп она справляется лучше случайной модели, но все еще недостаточно хорошо.

На мой взгляд, систему можно улучшить если собрать дополнительную информацию о водителях, к примеру:

- Водительский стаж
- Возраст водителя
- Семейное положение
- Необходимо дополнить признак состояния участника: (физическое или с учётом принятых лекарств) сейчас слишком много пропусков
- Возможно информация об уровне пробок по выбранному маршруту тоже может быть полезной





