# Предсказание склонности клиента к покупке
**Разработчик:** Команда "Sweepnet"

 ## Описание задачи

Предсказание склонности клиента к покупке — важная задача для многих компаний, позволяющая повысить эффективность рекомендаций и конверсию в покупку. При совместном использовании данных из различных источников можно составить более полный портрет клиента и более точные рекомендации.
## Цель

Необходимо разработать мультимодальную модель, позволяющую прогнозировать выдачу продуктов в течение следующего месяца. Обязательное условие: использование библиотеки PyTorch-LifeStream в решении задачи.
## Структура проекта

**Препроцессинг:**

    Preprocessor_geo.ipynb - препроцессинг на PySpark для данных по геохешей.
    Preprocessor_trx.ipynb - препроцессинг на PySpark для данных по транзакцияи.
    Train_emb_new.ipynb - генерация эмбеддингов транзакций при помощи Pytorch-LifeStream.
    Train_emb_geo.ipynb - генерация эмбеддингов геохешей при помощи Pytorch-LifeStream.
    dialog_preprocessing.ipynb - генератор фичей на основе эмбеддингов.
    compression_data.py - модуль по сжатию данных без потери данных (за счет умного изменения типа данных для каждой колонки).
    gen_sample_pairs_Client_Month.ipynb - кастомный сэмплер для оптимальной выборки пар клиент-месяц. (см. раздел Дисбаланс).
    create_normalize_trx.ipynb - нормализация цен транзакций за счет использования открытых данных ЦБ России по инфляции и курсам валют. (см. раздел Внешние источники данных).
    calc_good_bad_cos_sim_v2.ipynb - модуль расчета средних "хороших" (когда покупали) и "плохих" (когда не покупали) векторов и расчет расстояния рассматриваемых объектов до "хороших"/"плохих" примеров. 
    create_geo_features.py - модуль по формированию гео-фичей. Формируются фичи относительно геохешей уровней 4/5/6, включая фичи: популярности геохешей у клиентов, покупающих продукты, количество уникальных пользователей геохешей, количество транзакций в рамках геохеша и т.д. 
    create_agg_geo_v7_1.ipynb - генератор расширенных фичей на основе ГЕО.
    create_agg_dialog_v7_2.ipynb - генератор расширенных фичей на основе диалогов.
    create_agg_trx_v7_1.ipynb - генератор расширенных фичей на основе транзакций.
    create_agg_ptls_v7_1.ipynb - генератор расширенных фичей на основе эмбеддингов.
    create_agg_target_v2.ipynb - генератор расширенных фичей на основе таргетов.
**Модeль:**

    Optuna_Ansamble.ipynb - ансамблевый метод с использованием Optuna.
    baseline_v1_8_7.ipynb - кросс-валидация и объединение всех фичей.  
**Данные:**

    client_without_dlg.csv - список клиентов, у которых нет диалогов.
    client_without_geo.csv - список клиентов, у которых нет гео-данных.
    client_without_trx.csv - список клиентов, у которых нет транзакций.
    list_uniq_client_target.csv - список уникальных клиентов.
    esult_sample_Client_Month_df_12_06_2024.parquet - расширенный сэмпл клиентов используемый для генерации эбеддингов.
   Ссылка для **[скачивания](https://disk.yandex.ru/d/D6HiwFPZa9LEOg)**

## Установка и использование

    Установите необходимые зависимости:

    pip install requirements.txt

## Используйте Jupyter notebooks для генерации и обработки фичей:

    jupyter notebook Preprocessor_geo.ipynb
    jupyter notebook Preprocessor_trx.ipynb
    jupyter notebook Train_emb_new.ipynb
    jupyter notebook Train_emb_geo.ipynb
    jupyter notebook dialog_preprocessing.ipynb
    jupyter notebook gen_sample_pairs_Client_Month.ipynb
    jupyter notebook create_normalize_trx.ipynb
    jupyter notebook calc_good_bad_cos_sim_v2.ipynb
    jupyter notebook create_geo_features.py
    jupyter notebook create_agg_geo_v7_1.ipynb
    jupyter notebook create_agg_dialog_v7_2.ipynb
    jupyter notebook create_agg_trx_v7_1.ipynb
    jupyter notebook create_agg_ptls_v7_1.ipynb
    jupyter notebook create_agg_target_v2.ipynb
 
## Используйте Jupyter notebooks для обучения модели:
    jupyter notebook Optuna_Ansamble.ipynb
    jupyter notebook baseline_v1_8_7.ipynb

## Контактная информация

Если у вас возникли вопросы, пожалуйста, свяжитесь с нами по адресу: [dimk88d@gmail.com].
