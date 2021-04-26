Отличия Trunk-based development от feature-подхода.

Feture-based development (FBD)
В основе FBD лежит идея ветвления. Добавление нового функционала и вся последующая работа над ним, происходит в отдельных ветках. При этом у нас есть основаная master-ветка, которая защищена от попадания в неё нерабочего кода.
Обычно выделяют следующие ветки:
develop - основная ветвь разработки;
feature - создаётся для каждой новой фичи, после прохождения code review мержится в develop;
release - ветвь для подготовки сборки к релизу;
master - ветка с полностью стабильным кодом, готовым к деплою;
hotfix - появляется для срочных исправлений критических багов master-ветки.


Главными отличительными особенностями для этого можно выделить следующее:
- работа над каждой фичей ведётся в отдельной изолированной ветке, при этом другие разработчики смогут ознакомится с ней только после прохождения review;
- долгое прохождение review, в том числе из-за размеров задач;
- множество конфликтов при слиянии веток, в связи с долгой разработкой.

Trunk-based development (TBD)
Основная идея данного подхода в том, что у нас есть только одна основная master-ветка разработки (от того и название trunk - ствол), а feature-ветви с новым функционалом живут не более двух дней. Наша master-ветка всегда готова к деплою, в независимости от готовности фич.
Особенностями этого подхода являются:
- feature flags, позволяющие включать и выключать фичи в любой момент, что даёт нам возможность деплоить код с недописанными частями;
- branch by abstraction, декомпозирование задач на множество маленьких кусочков абстракций, что даёт очень частые интеграции, возможность быстро переключаться между задачами;
- continuous code review, очень маленький pull request (несколько минут), т.к. очень маленькие кусочки кода, что даёт постоянный шаринг знаний внутри команды и сильно ускоряет поставку в прод;

Но при этом, введение TBD требует высокое покрытие тестами, чтобы была возможность непрерывно мержить изменения в master, без опасности что-то сломать. Работа с feature flags заставит произвести изменения в инфраструктуре, потому как нужно реализовывать возможность включения и отключения фич в нашем коде. Необходимо умение построение абстракций и декомпозиции задач, для разбивки их на маленькие части.

Вывод
TBD имеет ряд неоспоримых преимуществ над FDB, но за них приходится расплачиваться высокими требованиями к более высокой квалификации разработчиков. В связи с этим, выбор конкретного подхода зависит от самого проекта и команды, работающей над ним.


