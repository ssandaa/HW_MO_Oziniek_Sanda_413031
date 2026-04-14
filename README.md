# Домашнее задание 3 — ансамбль, подбор гиперпараметров и интерпретация модели

Задача: бинарная классификация по датасету `Breast Cancer Wisconsin (Diagnostic):` предсказание `diagnosis (M — malignant, B — benign)` по числовым признакам.

Что сделано в работе:

разбиение на обучающую и тестовую выборки (`train_test_split`, `test_size=0.2`, `stratify=y`, `random_state=42`);
обучаемая модель: `HistGradientBoostingClassifier` (ансамбль деревьев);
подбор гиперпараметров: `RandomizedSearchCV` на стратифицированной кросс-валидации (`StratifiedKFold`, 5 фолдов, `scoring="recall"`);
обучение финальной модели с лучшими гиперпараметрами (`best_estimator_`);
оценка на отложенной выборке;
основная метрика: `Recall(M)` при кодировании `M => 1`, `B => 0` `(recall_score(..., pos_label=1))`, дополнительно `Precision(M)` и `F2(M)`;
интерпретация модели: глобальная (`Permutation Importance`, `SHAP summary`) и локальная (`SHAP waterfall` для отдельных объектов).
