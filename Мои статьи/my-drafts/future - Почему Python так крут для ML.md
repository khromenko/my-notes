---
tags:
  - Python
  - ML
Аудитория: Новичок
Время на чтение:
Дата создания:
---


Для тех кто как я только начала открывать мир ML и работы с данными, но ранее работал с java
Чем меня так удивил/поразили инструменты Python - numpy, pandas, mathplotlib, seaborn

---
# Библиотеки pandas, numpy
- быстрые операции над массивами данных/матрицами (яля продвинутый excel) с очень простым и лаконичным синтаксисом
	- пересечение, отбор, группировка
	- умножение, сложение
	- статистические характеристики					
- примеры
	- user_features["books_per_year"] = user_features["books_read"] / user_features["reading_years"]
- можно спокойно прокручивать датасеты с десятками миллионов записей и десятком столбцов (несколько секунд)
	- interactions - 222.629.898 - 222 миллиона записей, 5.4 Gb занимает памяти
	- группировки 
		- приведение даты к границе месяца, и агрегация данных истории по месяцам 
		- interactions_by_month = interactions
			.groupby(interactions['started_at'].dt.to_period('M'))
			.agg(
				events=('started_at', 'count'), 
				users=('user_id', 'nunique'), 
				tracks=('track_id', 'nunique')
			)
			.reset_index()
		- на ВМ - 4 CPU, 32 GB памяти - отработало за 1 мин 58 сек (VS Code Jupiter noteebok потреблял 10-20Gb памяти в процессе работы)
	- отбор топ-k объектов по пользователю
		- recs_for_common_users = recs_for_common_users.groupby("user_id").head(top_k)
# Построение графиков seaborn
	- красивые визуализации данных и их зависимостей