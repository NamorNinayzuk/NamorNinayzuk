
Задача 1

Опишите кратко, как вы поняли: в чем основное отличие полной (аппаратной) виртуализации, паравиртуализации и виртуализации на основе ОС.

Ответ: Технической реализации, полная виртуализация выглядит как: Сервер("железо") на котором стоит виртуалка с гипервизором. И через гипервизор реализовывается управлением виртуальных машин. Паравиртуализация: Сервер(железо) на котором развернутое ОС, на котором ставится виртуальное приложение в которое вмешается гипервизор и виртуальные машинки. Виртуализация на ОС отличается от последнего тем что использует контейнеры вместо виртуальных машин, и одно свое ядро ОС.

Доп.вопрос:В чём разница при работе с ядром гостевой ОС для полной и паравиртуализации?
Ответ: Паравиртуализация дает возможность создовать гостевую ОС даже на процессорах, не поддерживающих виртуализацию, т.е. при полной виртуализации немодифицированная гостевая ОС работает так же как была не виртуализирована, а вызовы ОС перехватывались и транслировались с использованием двоичного преобразования. В паравиртуализации ОС "знает" что она виртуализирована и взаимодействует с гипервизором.


Задача 2

Выберите один из вариантов использования организации физических серверов, в зависимости от условий использования.

Организация серверов:

    физические сервера,
    паравиртуализация,
    виртуализация уровня ОС.

Условия использования:

    Высоконагруженная база данных, чувствительная к отказу.
    Различные web-приложения.
    Windows системы для использования бухгалтерским отделом.
    Системы, выполняющие высокопроизводительные расчеты на GPU.

Опишите, почему вы выбрали к каждому целевому использованию такую организацию.

Ответ: Простите коллеги, но вопрос слегка некорректен. Для использования физ.серверов нужно выбрать условия? То тут зависимость от бизнеса и цели подойдут все условия. Или цель вопроса заключается в том что при каких условиях целесообразно использовать ту или иную форму виртуализации?

А по факту надо еще рассматривать и финансовую сторону, сторону нагрузки со стороны бизнеса.

При использовании высоконагруженной базы данных чувствительной к отказу – нужно организовать физические сервера, это и безопасней, и экономичней при ресурсных затратах.
Различные web-приложения – паравиртуализация. Только при использование систем ОКС,  EVE и Moody. В остальных достаточно виртуализации уровня ОС. 
При использовании Windows системы для бухгалтерских операций лучше использовать паравиртуализацию ибо для использования различных ОС это наиболее лучший выбор.
Системы, выполняющие высокопроизводительные расчеты на GPU - Виртуализация ОС, т.к. есть родной доступ к GPU



Задача 3

Выберите подходящую систему управления виртуализацией для предложенного сценария. Детально опишите ваш выбор.

Сценарии:

    100 виртуальных машин на базе Linux и Windows, общие задачи, нет особых требований. Преимущественно Windows based инфраструктура, требуется реализация программных балансировщиков нагрузки, репликации данных и автоматизированного механизма создания резервных копий.

Ответ: vmware esxi - Позволит почти безгранично создавать ВМ в отличии от Hyper-V, легок в настройке репликации и создания резервных копий.

Требуется наиболее производительное бесплатное open source решение для виртуализации небольшой (20-30 серверов) инфраструктуры на базе Linux и Windows виртуальных машин.

Ответ: QEMU с модулем kqemu либо Virtualbox - достаточен и прост в управлении для небольшого количества ВМ

Необходимо бесплатное, максимально совместимое и производительное решение для виртуализации Windows инфраструктуры.

Ответ: Hyper-V - родная для Винды, уже идет в комплекте с серверной ОС (почти всегда), но нужно смотреть лицензионное соглашение по эксплуатации и разворачиванию в зависимости от ядер и потоков

Необходимо рабочее окружение для тестирования программного продукта на нескольких дистрибутивах Linux.

Ответ: AlphaVM-Free - для исследований или KVM - для работы или User-mode Linux - истинных гурманов

Задача 4

Опишите возможные проблемы и недостатки гетерогенной среды виртуализации (использования нескольких систем управления виртуализацией одновременно) и что необходимо сделать для минимизации этих рисков и проблем. Если бы у вас был выбор, то создавали бы вы гетерогенную среду или нет? Мотивируйте ваш ответ примерами.

Ответ: гетерогенная среда виртуализации предполагает использования различных продуктов виртуализации от разных вендоров, что приведет к осложнению перемещению ВМ или контейнеров между этими средами, а так же наличию в штате людей которые будут знать досконально как эти системы работают между собой. Для минимизации рисков я бы выбрал лишь одну среду обитания ВМ и перевел бы все туда. гетерогенная среда необходима лишь в краткосрочный период, переходный от переноса системы с физических носителей в виртуальную среду, при наличии разношерстных ОС и "зоопарка" серверов и ПО.
