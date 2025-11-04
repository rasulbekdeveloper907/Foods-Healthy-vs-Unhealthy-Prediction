# 🧾 Dataset haqida — `df` ma’lumotlar to‘plami

## 📌 Umumiy ma’lumot

Ushbu `df` ma’lumotlar to‘plami **13 120 ta yozuv (satrlardan)** iborat bo‘lib, har bir satr **bitta mahsulot**ni ifodalaydi.  
Ma’lumotlar **Supervised Machine Learning (SML)** loyihasida ishlatiladi va **multi-class classification** uchun tayyorlangan.

🎯 **Target ustun:** `nova_group`  
Bu ustun mahsulotning **qayta ishlanish darajasini** bildiradi (masalan: tabiiy, qisman qayta ishlangan, to‘liq qayta ishlangan va h.k.).

---

## 📊 Dataset tuzilmasi

| # | Ustun nomi | Ma’lumot turi | Tavsif |
|---|-------------|----------------|--------|
| 1 | `Unnamed: 0.1` | `int64` | Texnik indeks (import jarayonida yaratilgan, ishlatilmaydi) |
| 2 | `Unnamed: 0` | `int64` | Texnik indeks (ishlatilmaydi, olib tashlanadi) |
| 3 | `name_length` | `float64` | Mahsulot nomining uzunligi (simvol soni) |
| 4 | `is_organic` | `float64` | Mahsulot organikmi (1 — ha, 0 — yo‘q) |
| 5 | `quantity_value` | `float64` | Mahsulot miqdorining sonli qiymati |
| 6 | `quantity_unit_encoded` | `float64` | Miqdor birligi (kodlangan shaklda) |
| 7 | `category_depth` | `float64` | Mahsulot kategoriyasining chuqurligi |
| 8 | `country_count` | `float64` | Mahsulot mavjud bo‘lgan davlatlar soni |
| 9 | `product_age_days` | `float64` | Mahsulot tizimga kiritilganidan beri o‘tgan kunlar soni |
| 10 | `created_month` | `float64` | Mahsulot tizimga qo‘shilgan oy (1–12) |
| 11 | `main_category_encoded` | `float64` | Asosiy kategoriya kodi |
| 12 | `nova_group` | `int64` | 🎯 Target ustun — mahsulotning qayta ishlanish darajasi |
| 13 | `y_true` | `int64` | Haqiqiy (testdagi) qiymatlar |
| 14 | `y_pred_ovo` | `int64` | One-vs-One modeli tomonidan bashorat qilingan qiymatlar |

---

## 📈 Dataset statistik ko‘rsatkichlari

| Ko‘rsatkich | Qiymat |
|--------------|--------|
| 🔢 Yozuvlar soni | 13 120 |
| 🧩 Ustunlar soni | 14 |
| 🧮 Raqamli ustunlar | 9 ta (`float64`) |
| 🔢 Butun sonli ustunlar | 5 ta (`int64`) |
| 🚫 Null qiymatlar | Yo‘q |
| ⚖️ Target sinflar soni | 4 (`nova_group` = {1, 2, 3, 4}) |

---

## 🧹 Ma’lumotni tozalash

Loyihada quyidagi tozalash bosqichlari bajarilgan:

1. **`Unnamed: 0`** va **`Unnamed: 0.1`** ustunlari olib tashlangan.
2. **`y_true`** va **`y_pred_ovo`** modelga kiritilmagan, faqat tahlil uchun ishlatilgan.
3. Ma’lumotlarda **bo‘sh (NaN)** qiymatlar aniqlanmadi.
4. **Turli o‘lchov birliklari (`quantity_unit_encoded`)** kodlangan.
5. **Raqamli ustunlar** (masalan `product_age_days`) normallashtirishga muhtoj emas, chunki model (Random Forest) masshtabga sezgir emas.

---

## 🔍 Ma’lumotlar tahlili (EDA qisqacha)

- `name_length` — qisqa nomli mahsulotlar ko‘p (moda 2–3 so‘zli nomlar).  
- `category_depth` — 1 dan 7 gacha bo‘lgan qiymatlar, o‘rta qiymat ≈ 4.  
- `country_count` — ko‘p mahsulotlar faqat 1 yoki 2 ta mamlakatda mavjud.  
- `product_age_days` — 0 dan 5000 kungacha, o‘rta qiymat ≈ 2500 kun.  
- `nova_group` — 4 sinfli target, lekin sinflar biroz nomutanosib (imbalanced).

---
