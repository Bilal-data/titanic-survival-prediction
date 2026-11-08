# Titanic Survival Prediction

A beginner machine-learning project on the Titanic dataset (891 passengers), built in Python (pandas, scikit-learn) on Google Colab. Goal: predict whether a passenger survived.

## Data cleaning

- Dropped `deck`: 688 of 891 values were missing (77 percent), so filling it would be mostly guessing.
- Filled the 177 missing `age` values with the median (28.0), which is less sensitive to very old passengers than the mean.
- Dropped `alive`: it is the same information as `survived` (data leakage). Keeping it would make the model look perfect without learning anything.
- Converted `sex` to numbers (male = 0, female = 1).

## Findings

| Group | Survival rate |
|---|---|
| Women | 74.2 percent |
| Men | 18.9 percent |
| First class | 63.0 percent |
| Second class | 47.3 percent |
| Third class | 24.2 percent |

Overall survival rate: 38.4 percent. These are correlations, not proof of cause (sex and class overlap).

## Model

Random Forest classifier (100 trees) on 6 features: `pclass`, `sex_num`, `age`, `fare`, `sibsp`, `parch`. 80/20 train/test split, random_state=42.

| Model | Accuracy on test set |
|---|---|
| Baseline (always predict "died") | 58.7 percent |
| Random Forest | 79.9 percent |

| Class | Precision | Recall |
|---|---|---|
| Died (0) | 0.82 | 0.84 |
| Survived (1) | 0.76 | 0.74 |

## Limitations

- The test set has only 179 passengers and a single split was used, so accuracy could move by several points with a different split.
- Missing ages were filled with one value, which shrinks the real spread of ages.
- No hyperparameter tuning and no cross-validation yet.
- Re-running on five other random splits gave accuracy between about 78 and 83 percent (average about 80), so the result is reasonably stable but not exact.

## Tools

Python, pandas, seaborn (dataset), scikit-learn, Google Colab.

---

## ملخص بالعربي

- الداتا فيها 891 راكب، والهدف توقع هل نجا الراكب.
- شلنا عمود `deck` لأن 77 بالمئة منه ناقص، وملّينا `age` بالوسيط.
- شلنا عمود `alive` لأنه نفس معلومة `survived` (تسريب إجابة).
- نسبة نجاة النساء 74 بالمئة والرجال 19 بالمئة، والدرجة الأولى 63 بالمئة والتالتة 24 بالمئة.
- النموذج `Random Forest` وصل لدقة 79.9 بالمئة، مقابل 58.7 بالمئة للنموذج الغبي (دايمًا مات).
- حدود النتيجة: اختبار على 179 راكب فقط وتقسيم واحد، فالرقم ممكن يتغير بعدة نقط.
