# Customer_outflow

Из «Бета-Банка» стали уходить клиенты. Каждый месяц. Немного, но заметно. Банковские маркетологи посчитали: сохранять текущих клиентов дешевле, чем привлекать новых.
Нужно спрогнозировать, уйдёт клиент из банка в ближайшее время или нет. Вам предоставлены исторические данные о поведении клиентов и расторжении договоров с банком.

При исследовании задачи мы выявили, что в целевом признаке имеется дисбаланс классов: 0 - 7963 (что составляет около 80%), 1 - 2037 (20%). Это может привести к тому, что модель будет предсказывать наиболее распространённый вариант ответа. В целом при борьбе с дисбалансом можно сделать следующие выводы:
- Самой лучшей моделью оказалась модель случайного леса при сбалансированном весе, которая на валидационной выборке при n_estimators = 92 и при max_depth = 9 показала значение f-1 = 0.633. AUC-ROC модели случайного леса на валидационной выборке: 0.855 при n_estimators = 94 при max_depth = 10;
- Модель случайного леса при увеличении выборки показала результаты на валидационной выборке чуть хуже - при n_estimators = 86 и при max_depth = 9 показала значение f-1 = 0.630, однако это чуть меньше, чем при сбалансированном весе - 0.633. AUC-ROC модели случайного леса на валидационной выборке: 0.854 при n_estimators = 89 при max_depth = 10, против 0.855 при сбалансированном весе;
- AUC-ROC модели случайного леса на валидационной выборке при дюбом способе практически одинаков: 0.851 при дисбалансе, 0.854 при увеличении и уменьшении выборки и 0.855 при сбалансированном классе;
- Модель логистической регрессии при борьбе с дисбалансом показала примерно одинаковый результат 0.487-0.49, однако это повысило показатель f-1, который составлял при дисбалансе 0.325. Однако F-1 мера все равно сильно меньше требуемого порога - 0.59.

Так как F-1 мера практически одинакова у модели случайного леса при сбалансированном весе и при увеличении выборки, протестируем эту модель 2 способами. Протестировав модели на тестовой выборке мы получили следующие показатели: 
- F-1 модели случайного леса на тестовой выборке при сбалансированном весе: 0.594 при n_estimators = 30 при max_depth = 8, AUC-ROC модели случайного леса на тестовой выборке при увеличении выборки: 0.849;
- F-1 модели случайного леса на тестовой выборке при увеличенной выборке: 0.616 при n_estimators = 83 при max_depth = 10, AUC-ROC модели случайного леса на тестовой выборке при увеличенной выборке: 0.855;
- F-1 случайной модели на тестовой выборке: 0.616.
