# Разработка сервиса для анализа тональности поисковой выдачи (SERP) в контексте оценки репутации бренда

## Описание проекта
![logo](./media/logo_project.png)

Проект представляет собой веб-сервис для анализа тональности поисковой выдачи (SERP) с целью оценки и мониторинга репутации бренда. Сервис автоматически собирает результаты поисковых систем по ключевым запросам, классифицирует их как позитивные / нейтральные / негативные, а затем визуализирует динамику изменений в выдаче на основе ТОП-20. В основе — использованием методов машинного обучения и обработки естественного языка (NLP).

Сервис помогает брендам:
- своевременно обнаруживать негативные упоминания, циркулирующие в поисковой выдаче;
- отслеживать, как меняется тональность контента в выдаче со временем;
- выявлять ключевые источники негативного воздействия;
- принимать обоснованные решения по управлению репутацией: вытеснение нежелательных ссылок, продвижение позитивных материалов, корректировка контентной стратегии.

---

## 🛠 Технологии и инструменты

### 🔧 Язык программирования
![Python](https://img.shields.io/badge/Python-3.13.0-blue?logo=python&logoColor=white)

### 📦 Менеджеры пакетов и среды
![pip](https://img.shields.io/badge/pip-%2300C7B7.svg?logo=pypi&logoColor=white)
![conda](https://img.shields.io/badge/conda-44A833.svg?logo=anaconda&logoColor=white)

### 🧪 Контроль версий и хостинг
![git](https://img.shields.io/badge/git-F05032.svg?logo=git&logoColor=white)
![GitHub](https://img.shields.io/badge/github-181717?logo=github&logoColor=white)
![dvc](https://img.shields.io/badge/DVC-945DD6.svg?logo=dvc&logoColor=white)

### 🧰 Шаблоны и стандарты кода
![cookiecutter](https://img.shields.io/badge/cookiecutter-FFD43B.svg?logo=cookiecutter&logoColor=black)
![flake8](https://img.shields.io/badge/flake8-008000.svg?logo=python&logoColor=white)
![black](https://img.shields.io/badge/black-000000.svg?logo=python&logoColor=white)

### 🧩 CLI и обработка аргументов
![click](https://img.shields.io/badge/click-FFD43B.svg?logo=python&logoColor=black)
![argparse](https://img.shields.io/badge/argparse-3776AB.svg?logo=python&logoColor=white)

### 📊 Машинное обучение и аналитика
![MLflow](https://img.shields.io/badge/MLflow-0194E2.svg?logo=mlflow&logoColor=white)
![catboost](https://img.shields.io/badge/CatBoost-FFCC00.svg?logo=python&logoColor=black)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E.svg?logo=scikitlearn&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-150458.svg?logo=pandas&logoColor=white)
![numpy](https://img.shields.io/badge/numpy-013243.svg?logo=numpy&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C.svg?logo=pytorch&logoColor=white)

### 🖥️ Автоматизация и тестирование
![pyautogui](https://img.shields.io/badge/pyautogui-3776AB.svg?logo=python&logoColor=white)
![pytest](https://img.shields.io/badge/pytest-0A9EDC.svg?logo=pytest&logoColor=white)

## Участники проекта (#16)

- Исполнитель: Молчанов Вячеслав - tg: @Crow0219, https://t.me/Crow0219
- Куратор: Неволина Арина - tg: @nevolinaa, https://github.com/nevolinaa

## 🗂️ Детальный план разработки проекта

---

### 1️⃣ Сбор данных и EDA (Exploratory Data Analysis) 🔍
- 🌐 Определить поисковые системы: **Google, Яндекс**  
- 🎯 Уточнить конечные результаты: *сервис + отчётность + экспериментальная часть*  
- ⚙️ Определить:
  - формат сервиса (**API/веб-дашборд**)  
  - режим работы (**батчевый + обновление данных**)  
  - требования к результатам инференса (тональность по ключам, общая картина, топ-негатив/позитив)  
- 📥 Настроить сбор SERP (через API или парсинг): запросы по ключевым словам, сбор **ТОП-20 страниц**  
- 🗄️ Разработать пайплайн для хранения данных: **PostgreSQL + DVC**  
- 📝 Собрать метаинформацию (датасет): адреса, заголовки, сниппеты, домены  
- 📊 Провести EDA:
  - распределение источников  
  - частота позитивных/негативных терминов  
  - анализ дубликатов  
  - длина и структура текстов  

---

### 2️⃣ Линейные модели ML (baseline) ⚡
- 🧮 Подготовить базовые модели: **логистическая регрессия, линейный SVM**  
- 🧩 Признаки: **Bag-of-Words, TF-IDF**  
- 📐 Метрики: **Accuracy, Precision, Recall, F1**  
- 🔎 Выявить слабые места baseline (*сарказм, контекст*)  

---

### 3️⃣ Нелинейные модели ML + Feature Engineering 🤖
- 🌲 Обучить и сравнить модели: **Random Forest, CatBoost, Gradient Boosting**  
- 🛠️ Feature engineering: биграммы/триграммы, эмбеддинги (**Word2Vec, fastText**)  
- 🔄 Провести кросс-валидацию  
- 🏆 Зафиксировать метрики и выбрать лучшее ML-решение для интеграции  

---

### 4️⃣ Создание сервиса 🖥️
- 🏗️ Архитектура:  
  - Backend → **FastAPI**  
  - Хранение → **PostgreSQL**  
  - Менеджмент экспериментов → **MLflow**  
- 🔌 API: ввод бренд-запроса → анализ + сохранение истории запросов  
- 📈 Визуализация (**Streamlit/Gradio**):  
  - распределение тональности по ключам  
  - общая картина по бренду  
  - топ негативных и позитивных страниц  
  - динамика по времени  
- 📦 Обернуть ML-модель в сервис (**Docker**)  

---

### 5️⃣ DL-модели 🧠
- 📚 Использовать предобученные трансформеры: **BERT/RuBERT, DistilBERT**  
- ⚖️ Сравнить DL и ML по метрикам и скорости  
- 🎛️ Провести тюнинг гиперпараметров (learning rate, batch size, sequence length)  
- 🚀 Оптимизировать инференс: **quantization, distillation**  

---
