# АНАЛИЗ ДАННЫХ В РАЗРАБОТКЕ ИГР [in GameDev]
Отчет по лабораторной работе #5 выполнил(а):
- Власова Елена Васильевна
- РИ230931
Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | * | 20 |
| Задание 3 | * | 20 |

знак "*" - задание выполнено; знак "#" - задание не выполнено;

Работу проверили:
- к.т.н., доцент Денисов Д.В.
- к.э.н., доцент Панов М.А.
- ст. преп., Фадеев В.О.

[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

Структура отчета

- Данные о работе: название работы, фио, группа, выполненные задания.
- Цель работы.
- Задание 1.
- Найдите внутри C# скрипта “коэффициент корреляции ” и сделать выводы о том, как он влияет на обучение модели.
- Задание 2.
- Изменить параметры файла yaml-агента и определить какие параметры и как влияют на обучение модели. Привести описание не менее трех параметров.
- Задание 3.
- Приведите примеры, для каких игровых задачи и ситуаций могут использоваться примеры 1 и 2 с ML-Agent’ом. В каких случаях проще использовать ML-агент, а не писать программную реализацию решения? 

- Выводы.
- ✨Magic ✨
# Машинное обучение в Unity. ML-Agent
# Цель работы : 
Познакомиться с программными средствами для создания системы машинного обучения и ее интеграции в Unity.
## Постановка задачи.
В данной лабораторной работе мы создадим ML-агент и будем тренировать нейросеть, задача которой будет заключаться в управлении шаром. Задача шара заключается в том, чтобы оставаясь на плоскости находить кубик, смещающийся в заданном случайном диапазоне координат.

## 1 Поиск агентом объекта на сцене

Реализация системы машинного обучения в связке Python - Google-Sheetes-Unity:
- Создание нового пустого 3D проекта на Unity под названием ML-Agent_GameDiva
- 
![Снимок экрана 2024-12-15 194740](https://github.com/user-attachments/assets/024b1d18-0e23-4d9d-bd82-45437a169842)

- Скачала папку из Workshop#5: ml-agents-release_19.
- В проекте на Unity я с помощью команд Window - Package Manager - раскрыв + - Add Package From Disk добавила два .json файла:
- ml-agents-release_19 / com,unity.ml-agents / package.json
- ml-agents-release_19 / com,unity.ml-agents.extensions / package.json

![Снимок экрана 2024-12-16 130146](https://github.com/user-attachments/assets/6fd1e80a-e831-48c6-a3b8-4d7689aede7c)

![Снимок экрана 2024-12-16 130850](https://github.com/user-attachments/assets/d9c9b684-d260-4132-8c96-45ffca51a24a)

Во вкладке Component появился ML-agent, значит всё сделано правильно.

![Снимок экрана 2024-12-16 131900](https://github.com/user-attachments/assets/93acde91-d5fc-4f7f-892e-fad8b31bdee0)

Запуск Anaconda Promt для дальнейшей работы:
- создание ML-агента под именем GameDiva
![Снимок экрана 2024-12-16 141936](https://github.com/user-attachments/assets/9e2d3a93-8fb0-4f21-bf58-4a261ae89d06)

- Подгрузка нужных файлов
- Активация ML-агента GameDiva
- Переход к работе сразу с папкой проекта Unity C:\Users\712\ML-Agent_GameDIva
![Снимок экрана 2024-12-16 141720](https://github.com/user-attachments/assets/59e7b40b-9f4d-474e-be71-70d371840f00)
- Установка библиотек

![Снимок экрана 2024-12-16 151254](https://github.com/user-attachments/assets/8c399b2d-ee6d-407c-9956-de650557f9c6)

![Снимок экрана 2024-12-16 151318](https://github.com/user-attachments/assets/a8e294b8-ebbc-4ea7-8420-7d9bd4ae2c1a)

![Снимок экрана 2024-12-16 154806](https://github.com/user-attachments/assets/5cd9d9d2-f4ce-4063-8983-600dcd4262b5)

- Создание на сцене плоскости, куба и сферы
- Создание C# скрипта и подключение его к сфере

![Снимок экрана 2024-12-16 163610](https://github.com/user-attachments/assets/8cc855c9-03be-4bad-940f-510fdeda6954)

- Доабвление кода к сфере из материалов лабораторных работ

![Снимок экрана 2024-12-16 164001](https://github.com/user-attachments/assets/c3e3ec13-c6e6-4be0-88ad-10510fb42b8f)

![Снимок экрана 2024-12-16 164007](https://github.com/user-attachments/assets/6d8985e6-2a3d-45a6-b0f9-370c67bc85f6)

- Добавление к сфере Rigitbody, Decision Requester, Behavior Parameters и их настройка

![Снимок экрана 2024-12-16 170045](https://github.com/user-attachments/assets/836e9bdb-f9e0-4f24-ad05-968cd9240c48)

![Снимок экрана 2024-12-16 170105](https://github.com/user-attachments/assets/2b01bb66-473f-46d8-bdee-891d46633531)

- Добавление в корень проекта файла конфигурации нейронной сети
## Задание 1
### Найдите внутри C# скрипта “коэффициент корреляции ” и сделать выводы о том, как он влияет на обучение модели.
    
Ход работы:


## Задание 2
### Изменить параметры файла yaml-агента и определить какие параметры и как влияют на обучение модели. Привести описание не менее трех параметров.

Ход работы:

## Задание 3
### Приведите примеры, для каких игровых задачи и ситуаций могут использоваться примеры 1 и 2 с ML-Agent’ом. В каких случаях проще использовать ML-агент, а не писать программную реализацию решения? 

Ход работы:

## Выводы

Абзац умных слов о том, что было сделано и что было узнано.

| Plugin | README |
| ------ | ------ |
| Dropbox | [plugins/dropbox/README.md][PlDb] |
| GitHub | [plugins/github/README.md][PlGh] |
| Google Drive | [plugins/googledrive/README.md][PlGd] |
| OneDrive | [plugins/onedrive/README.md][PlOd] |
| Medium | [plugins/medium/README.md][PlMe] |
| Google Analytics | [plugins/googleanalytics/README.md][PlGa] |

## Powered by

**BigDigital Team: Denisov | Fadeev | Panov**
