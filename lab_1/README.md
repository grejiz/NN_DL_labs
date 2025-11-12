# ЛР1 БыковаДО ГР6232

## Краткий обзор выбранной модели 

YOLO - модель (семейство моделей) глубокого обучения, направленная на детекцию объектов на изображении (в данной лабораторной предобученная модель могла разисать 80 классов). В процессе детекции определяется класс, границы объекта и вероятность принадлежности класса.

YOLO относится к one-stage детектором, то есть изображение пропускается через нейронку 1 раз, предсказывая одновременно координаты объекта и класс.Точность чуть ниже чем у two-stage детекторов, при этом выше скорость детекции. 

Работает так: делит изображение на сетку -> для каждой ячейки сетки модель предсказывает рамки (bounding boxes), наличие объекта и его класс.

Как я поняла, модель можно использовать так: дообучить на узкоспециализированном наборе данных  и использовать в конкретной предметной области (в которой, например, требуется детекция в реальном времени).
___

Основная работа была проделана в файле [6232_БыковаДО_lab1_detection.ipynb](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/6232_БыковаДО_lab1_detection.ipynb), но дообучать модель в колабе или на своем компе было оооооочень долго, поэтому было принято решение отдать эту задачу человеку с нормальным компьютером (я ему прислала файл: [notebook.ipynb](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/notebook.ipynb)), он вернул мне модель и я продолжила работать в первом файле.
___

## Иллюстрации работы до и после дообучения

Для дообучения я выбрала 5 класссов из датасета COCO: {0: 'person', 1: 'car', 2: 'dog', 3: 'cat', 4: 'bicycle'}. А также я сократила датасет до примерно 100 экземпляров на класс, чтобы побыстрее обучилось. Наверное, если бы я этого не сделала, результат был бы лучше, но проверять я это не буду.

После дообучения модель детектит эти 5 классов. Судя по иллюстрациям, точность после дообучения не ниже чем до дообучения.

| До обучения | После обучения |
|-------------|----------------|
|![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/%D0%94%D0%BE%20%D0%BE%D0%B1%D1%83%D1%87%D0%B5%D0%BD%D0%B8%D1%8F/tmp2qbfi6_c.PNG)|![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/%D0%9F%D0%BE%D1%81%D0%BB%D0%B5%20%D0%BE%D0%B1%D1%83%D1%87%D0%B5%D0%BD%D0%B8%D1%8F/tmpwplsmlai.PNG)|
|![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/%D0%94%D0%BE%20%D0%BE%D0%B1%D1%83%D1%87%D0%B5%D0%BD%D0%B8%D1%8F/tmpa47smg_s.PNG)|![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/%D0%9F%D0%BE%D1%81%D0%BB%D0%B5%20%D0%BE%D0%B1%D1%83%D1%87%D0%B5%D0%BD%D0%B8%D1%8F/tmp3wtk9y3b.PNG)|
|![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/%D0%94%D0%BE%20%D0%BE%D0%B1%D1%83%D1%87%D0%B5%D0%BD%D0%B8%D1%8F/tmpb8t9uo6_.PNG)|![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/%D0%9F%D0%BE%D1%81%D0%BB%D0%B5%20%D0%BE%D0%B1%D1%83%D1%87%D0%B5%D0%BD%D0%B8%D1%8F/tmprfq6y11t.PNG)|
|![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/%D0%94%D0%BE%20%D0%BE%D0%B1%D1%83%D1%87%D0%B5%D0%BD%D0%B8%D1%8F/tmpcaq_c4xc.PNG)|![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/%D0%9F%D0%BE%D1%81%D0%BB%D0%B5%20%D0%BE%D0%B1%D1%83%D1%87%D0%B5%D0%BD%D0%B8%D1%8F/tmpb94cwh1d.PNG)|
|![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/%D0%94%D0%BE%20%D0%BE%D0%B1%D1%83%D1%87%D0%B5%D0%BD%D0%B8%D1%8F/tmpccie4xtc.PNG)|![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/%D0%9F%D0%BE%D1%81%D0%BB%D0%B5%20%D0%BE%D0%B1%D1%83%D1%87%D0%B5%D0%BD%D0%B8%D1%8F/tmp35qp_gp8.PNG)|
|![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/%D0%94%D0%BE%20%D0%BE%D0%B1%D1%83%D1%87%D0%B5%D0%BD%D0%B8%D1%8F/tmpi3jbtoqh.PNG)|![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/%D0%9F%D0%BE%D1%81%D0%BB%D0%B5%20%D0%BE%D0%B1%D1%83%D1%87%D0%B5%D0%BD%D0%B8%D1%8F/tmprppoljd4.PNG)|
|![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/%D0%94%D0%BE%20%D0%BE%D0%B1%D1%83%D1%87%D0%B5%D0%BD%D0%B8%D1%8F/tmpsfqw4624.PNG)|![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/%D0%9F%D0%BE%D1%81%D0%BB%D0%B5%20%D0%BE%D0%B1%D1%83%D1%87%D0%B5%D0%BD%D0%B8%D1%8F/tmptskpi7d2.PNG)|
|![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/%D0%94%D0%BE%20%D0%BE%D0%B1%D1%83%D1%87%D0%B5%D0%BD%D0%B8%D1%8F/tmptf06g3cg.PNG)|![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/%D0%9F%D0%BE%D1%81%D0%BB%D0%B5%20%D0%BE%D0%B1%D1%83%D1%87%D0%B5%D0%BD%D0%B8%D1%8F/tmpo8vyp6ci.PNG)|

## Графики с результатами

Метрика mAP при разных IoU порогах:
![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/mAP_vs_IoU.png)

Прочие графики при разных IoU порогах:

| IoU  | Матрица ошибок | Precision | Recall |
| ---- | -------------- | --------- | ------ |
| 0.50 | ![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/val6/confusion_matrix_normalized.png)  | ![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/val6/BoxP_curve.png)  | ![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/val6/BoxR_curve.png)  |
| 0.55 | ![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/val7/confusion_matrix_normalized.png)  | ![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/val7/BoxP_curve.png)  | ![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/val7/BoxR_curve.png)  |
| 0.60 | ![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/val8/confusion_matrix_normalized.png)  | ![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/val8/BoxP_curve.png)  | ![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/val8/BoxR_curve.png)  |
| 0.65 | ![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/val9/confusion_matrix_normalized.png)  | ![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/val9/BoxP_curve.png)  | ![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/val9/BoxR_curve.png)  |
| 0.70 | ![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/val10/confusion_matrix_normalized.png) | ![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/val10/BoxP_curve.png) | ![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/val10/BoxR_curve.png) |
| 0.75 | ![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/val11/confusion_matrix_normalized.png) | ![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/val11/BoxP_curve.png) | ![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/val11/BoxR_curve.png) |
| 0.80 | ![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/val12/confusion_matrix_normalized.png) | ![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/val12/BoxP_curve.png) | ![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/val12/BoxR_curve.png) |
| 0.85 | ![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/val13/confusion_matrix_normalized.png) | ![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/val13/BoxP_curve.png) | ![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/val13/BoxR_curve.png) |
| 0.90 | ![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/val14/confusion_matrix_normalized.png) | ![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/val14/BoxP_curve.png) | ![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/val14/BoxR_curve.png) |
| 0.95 | ![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/val15/confusion_matrix_normalized.png) | ![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/val15/BoxP_curve.png) | ![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/val15/BoxR_curve.png) |


## Ответы на контрольные вопросы
1. Чем one-stage детекторы отличаются от two-stage?

One-stage детекторы пропускают изображение через модель один раз, работает быстрее, но менее точно определяет класс объекта. 

Two-stage детекторы состоят из 2х специализированных модулей. Скачала нейросеть определяет потенциальные регионы, затем каждый регион отправляется к модуль-классификатор, где производится определение класса и уточняет координаты объекта. Работает менее быстро, но более точно.

2. Какие ошибки чаще всего допускает модель при детекции?

Плохо детектим маленькие объекты (так в интернете написан, на примерах не обратила внимание), иногда неверно определяет объект или не определяет объект вовсе ([пример: собака (наверное это собака) вообще не определяется, и какой то кружочек определяется как велик](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/%D0%9F%D0%BE%D1%81%D0%BB%D0%B5%20%D0%BE%D0%B1%D1%83%D1%87%D0%B5%D0%BD%D0%B8%D1%8F/tmp35qp_gp8.PNG)).
Может увидеть объект там, где его нет или ошибиться с границами объекта. Пример с границами:

| До обучения | После обучения |
|-------------|----------------|
|![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/%D0%94%D0%BE%20%D0%BE%D0%B1%D1%83%D1%87%D0%B5%D0%BD%D0%B8%D1%8F/tmp2qbfi6_c.PNG)|![](https://github.com/grejiz/NN_DL_labs/blob/main/lab_1/%D0%9F%D0%BE%D1%81%D0%BB%D0%B5%20%D0%BE%D0%B1%D1%83%D1%87%D0%B5%D0%BD%D0%B8%D1%8F/tmpwplsmlai.PNG)|
