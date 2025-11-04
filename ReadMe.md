# 🧠 SML Multi-Class Classification — Target: `nova_group`

## 📋 Loyihaning maqsadi
Ushbu loyiha **Supervised Machine Learning (SML)** yondashuvi asosida qurilgan **multi-class classification** masalasidir.  
Modelning asosiy maqsadi — **mahsulotlar haqidagi turli atributlar (features)** asosida `nova_group` ni **aniq tasniflash** (classification)dir.

`nova_group` ustuni — bu mahsulotlarning **qayta ishlanish darajasini** ifodalaydi (masalan, tabiiy, qisman qayta ishlangan, to‘liq qayta ishlangan va h.k.).  
Bu tahlil orqali oziq-ovqat mahsulotlarini ularning **ishlov darajasi bo‘yicha guruhlash** mumkin bo‘ladi.

---

## 📦 Dataset haqida

Ushbu loyiha uchun **13 120 ta yozuv (sample)** dan iborat ma’lumotlar to‘plami ishlatilgan.  
Har bir satr — bu **bitta mahsulot** bo‘lib, u haqida turli **raqamli va kategorik ma’lumotlar** mavjud.

| # | Ustun nomi | Tavsif |
|---|-------------|--------|
| 1 | name_length | Mahsulot nomining uzunligi (simvol soni) |
| 2 | is_organic | Organik mahsulotmi (1 — ha, 0 — yo‘q) |
| 3 | quantity_value | Mahsulot miqdori qiymati |
| 4 | quantity_unit_encoded | Miqdor birligi (kodlangan ko‘rinishda) |
| 5 | category_depth | Kategoriya chuqurligi (qanchalik pastki kategoriya ekanligi) |
| 6 | country_count | Mahsulot mavjud bo‘lgan davlatlar soni |
| 7 | product_age_days | Mahsulot tizimga qo‘shilganidan beri o‘tgan kunlar soni |
| 8 | created_month | Mahsulot qo‘shilgan oy |
| 9 | main_category_encoded | Asosiy kategoriya kodi |
| 10 | nova_group | 🎯 **Target ustun** (model aniqlashi kerak bo‘lgan toifa) |
| 11 | y_true | Sinovdagi haqiqiy qiymatlar |
| 12 | y_pred_ovo | Oldingi OVO model natijalari |
| 13 | Unnamed: 0, Unnamed: 0.1 | Texnik indeks ustunlari (ishlatilmaydi) |

---

## 🧩 Ma’lumotlarni tayyorlash (EDA – Exploratory Data Analysis)

Tahlil jarayonida quyidagi qadamlar bajarilgan:

1. **Null qiymatlar** tekshirildi → Dataset toza (null yo‘q).
2. **Ustun turlari** (`int`, `float`, `object`) tahlil qilindi → 9 ta raqamli, 0 ta matnli.
3. **Ta’sirli ustunlar** aniqlanib, ba’zilari qo‘shimcha tarzda yaratilgan:
   - `life_span_log`, `birth_year_boxcox`, `occupation_cluster` kabi **transformatsiyalangan xususiyatlar**.
4. **Outlier** (g‘ayritabiiy qiymatlar) analiz qilinib, kerakli tozalash ishlari bajarilgan.
5. **Feature scaling** zarur bo‘lmagan, chunki `RandomForest` masshtabga sezgir emas.

---

## 🧠 Model haqida

Model sifatida **RandomForestClassifier** tanlandi, chunki u:
- Ko‘p sinfli (multi-class) muammolarni yaxshi hal qiladi,
- Kategorik va raqamli xususiyatlarni birlashtira oladi,
- Overfitting’ga nisbatan barqaror.