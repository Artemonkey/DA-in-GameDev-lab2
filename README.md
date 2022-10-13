# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #2 выполнил(а):
- Ямбушев Артём Дамирович
- РИ210933
Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | # | 20 |
| Задание 3 | # | 20 |

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
- Задание 1.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Задание 2.
- Задание 3.
- Выводы.
- ✨Magic ✨

## Цель работы
Познакомиться с программными средствами для организции передачи данных между инструментами google, Python и Unity

## Задание 1
### Реализовать совместную работу и передачу данных в связке Python - Google-Sheets – Unity.
Ход работы:
- В облачном сервисе google console подключил API для работы с google sheets и google drive.
- Далее реализовал запись данных из скрипта на python в google-таблицу. Данные описывают изменение темпа инфляции на протяжении 11 отсчётных периодов, с учётом стоимости игрового объекта в каждый период.
- Вывод кода и сама таблица:
![image](https://user-images.githubusercontent.com/101344196/195162415-e9184427-b031-4e16-96f9-b3ee4f7e0b6d.png)
- Код:
```py
import gspread
import numpy as np
gc = gspread.service_account(filename='striking-port-365214-1c881f3f82c2.json')
sh = gc.open("UnitySheets")
price = np.random.randint(2000, 10000, 11)
mon = list(range(1,11))
i = 0
while i <= len(mon):
    i += 1
    if i == 0:
        continue
    else:
        tempInf = ((price[i-1]-price[i-2])/price[i-2])*100
        tempInf = str(tempInf)
        tempInf = tempInf.replace('.',',')
        sh.sheet1.update(('A' + str(i)), str(i))
        sh.sheet1.update(('B' + str(i)), str(price[i-1]))
        sh.sheet1.update(('C' + str(i)), str(tempInf))
        print(tempInf)
```
- Создал новый проект на Unity, который будет получать данные из google-таблицы, в которую были записаны данные в предыдущем пункте.
- Написал функционал на Unity, в котором будет воспризводиться аудио-файл в зависимости от значения данных из таблицы.
- В итоге всё зароботало:
![image](https://user-images.githubusercontent.com/101344196/195180301-b83d8edf-bc8d-466c-9608-89e46c83ff71.png)
- Решил обновить данные в google-таблице заново запустив python-код. На скриншоте представлены новые значения:
![image](https://user-images.githubusercontent.com/101344196/195180711-7e52d5e0-3e90-4678-880c-b8f1f7a44b70.png)
- Результат выполнения программы в Unity с новыми данными. Смущает количество ошибок в начале, но он работает:
![image](https://user-images.githubusercontent.com/101344196/195180926-e3baca07-1058-4f8f-abe6-074bc1c00c3d.png)

## Задание 2

## Задание 3

## Выводы

Познакомился с программными средствами для организции передачи данных между инструментами google, Python и Unity. Понял насколько это кропотливый труд

## Powered by

**BigDigital Team: Denisov | Fadeev | Panov**
