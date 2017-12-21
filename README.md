# Нет Х-у У-а
### Материалы
https://docs.google.com/spreadsheets/d/1E64wvkk2v_QdicXbSs6mfdoupKG1As8w3qRO5PDqaDI/edit#gid=1741419272

## Рабочая гипотеза

В русском языке существует конструкция "Нет Х-у У-а", которая встречается только с ограниченным лексическим набором


### Материал исследования
200 примеров взято из НКРЯ. Запросом послужил заданный определнный порядок нет + (S|SPRO),dat + (S|SPRO),gen

### Факторы выбора конструкции
Фактором выбора конструкции послужила рефлексивизация субъетка. В выборке встретилось много шума, не относящегося к данной конструкции, например "В газете нет тебя", подходящего по грамматическим параметрам, но не подходящего по конструкции. От такого шума пришлось избавляться.

## Анализ: дескриптивная статистика
Общий анализ лексемного состава конструкции заключался прежде всего в оценке лексем первой ее части, так как имеено там большой разброс.Разница в предикатах особа не видна.

![Снимок экрана 2017-12-21 в 11.07.32](https://github.com/vitiushik/Project/blob/master/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202017-12-21%20%D0%B2%2011.07.32.png "Снимок экрана 2017-12-21 в 11.07.32")

![Снимок экрана 2017-12-21 в 11.10.21](https://github.com/vitiushik/Project/blob/master/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202017-12-21%20%D0%B2%2011.10.21.png "Снимок экрана 2017-12-21 в 11.10.21")


## Лингвистический анализ результатов статистического анализа
Результаты теста хи-квадрат. Корреляция выбора части речи субъекта в зависимости от порядка слов

data = read.csv(file='/Users/viktoriapirogova/Desktop/xy.csv', sep=',', header = T)
xy.no.n <- sum(data[data$order =='xy.no',]$arg0.part)
xy.no.pr <- nrow(data[data$order =='xy.no',]) - xy.no.n

no.xy.n <- sum(data[data$order =='no.xy',]$arg0.part)
no.xy.pr <- nrow(data[data$order =='no.xy',]) - no.xy.n
 
xy.no <- c(noun=xy.no.n, pronoun=xy.no.pr)
no.xy <- c(noun=no.xy.n, pronoun=no.xy.pr)
df = as.data.frame(rbind(xy.no, no.xy))
chisq.test(df)

data:  df
X-squared = 12.248, df = 1, p-value = 0.0004658

      noun pronoun
xy.no   40      21
no.xy   71       7

Поскольку получившееся значение p-value < 0.001, это позволяет нам сделать вывод о том, что тип конструкции связан с частью речи первой переменной: конструкция "Нет Х-у У-а" больше тяготеет к сочетанию с существительными, чем конструкция "Х-у нет У-а".

Есть ли корреляция между частью речи и числом?

data = read.csv(file='/Users/viktoriapirogova/Desktop/xy.csv', sep=',', header = T)
head(data)

pr.sg <- sum(data[data$arg0.part =='pr',]$arg0.numb)
pr.pl <- nrow(data[data$arg0.part =='pr',]) - pr.sg

no.sg <- sum(data[data$arg0.part =='n',]$arg0.numb)
no.pl <- nrow(data[data$order =='n',]) - no.sg

pr <- c(sg=pr.sg, pl=pr.pl)
n <- c(sg=no.sg, pl=no.pl)
df = as.data.frame(rbind(noun, pronoun))
chisq.test(df)
df

X-squared = 11.342, 
df = 1, 
p-value =  0.542 > 0.005.
Следовательно корреляции между частью речи (существительное или местоимение) и числом нет

