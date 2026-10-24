# Лекция 7. Качество и тестирование моделей.

**Ссылка на рабочий ноутбук:** [Наш Google Colab с pytest-тестами](https://colab.research.google.com/drive/1RH2bSDuFodvHRIt-zW4BphqigPs0HU2z?usp=sharing)

## Отчёт по тестированию

**Данные:**
- Train: 2250 объектов
- Test: 750 объектов
- Доля фрода в train: 15.8%

**Метрики на тесте:**

| Метрика | Значение |
|---|---:|
| Accuracy | 0.9227 |
| F1-score | 0.7010 |
| ROC-AUC | 0.9420 |
| Precision | 0.9067 |
| Recall | 0.5714 |

**Classification report:**

```text
              precision    recall  f1-score   support

       legit      0.924     0.989     0.956       631
       fraud      0.907     0.571     0.701       119

    accuracy                          0.923       750
   macro avg      0.916     0.780     0.828       750
weighted avg      0.922     0.923     0.915       750
```

**Результаты проверок:**

| Проверка | Статус |
|---|---|
| [OK] Предсказания работают | PASS |
| [OK] Форма и значения корректны (0/1) | PASS |
| [OK] Вероятности в [0, 1] | PASS |
| [OK] Модель не trivial (оба класса) | PASS |
| [OK] F1 >= 0.70 | PASS |
| [OK] ROC-AUC >= 0.85 | PASS |
| [OK] Precision >= 0.80 | PASS |
| [OK] Recall >= 0.55 | PASS |
| [OK] Есть feature_importances_ | PASS |

**ИТОГ:** все проверки пройдены

**Главное слабое место:** Recall ≈ 0.57 — модель пропускает часть фрода.  
**Рекомендация:** `class_weight='balanced'` или подбор threshold.
