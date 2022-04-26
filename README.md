# MTS Kata "Шпаргалки" от команды Танго

- [Наша команда](https://gitlab.services.mts.ru/avendour/archkata#наша-команда)
- [Глоссарий](https://gitlab.services.mts.ru/avendour/archkata#глоссарий)
- [Вводные](https://gitlab.services.mts.ru/avendour/archkata#вводные)
- [Бизнес сценарии и цели](https://gitlab.services.mts.ru/avendour/archkata#бизнес-сценарии-и-цели)
- [Стейкхолдеры](https://gitlab.services.mts.ru/avendour/archkata#стейкхолдеры)
- [Требования к системе](https://gitlab.services.mts.ru/avendour/archkata#границы)
    - [Допущения](https://gitlab.services.mts.ru/avendour/archkata#допущения)
    - [Границы решения](https://gitlab.services.mts.ru/avendour/archkata#требования-к-системе)
    - [Функциональные](https://gitlab.services.mts.ru/avendour/archkata)
    - [Атрибуты качества](https://gitlab.services.mts.ru/avendour/archkata#атрибуты-качества)
- [Architecture Decision Records](https://gitlab.services.mts.ru/avendour/archkata#architecture-decision-records)
- [Архитектура](https://gitlab.services.mts.ru/avendour/archkata#архитектура)
    -   [Контекст системы](https://gitlab.services.mts.ru/avendour/archkata#контекст-системы)
    -   [Контейнерная диаграмма](https://gitlab.services.mts.ru/avendour/archkata#контейнерная-диаграмма)
    -   [Компонентная диаграмма](https://gitlab.services.mts.ru/avendour/archkata#компонентная-диаграмма)


## Наша команда
![](res/logo.png)

***Члены команды:***
**Александр, Павел, Максим, Татьяна**

**Кто мы:**  мы коллеги разных команд, но одной компании, что нас и объединяет. Мы разные, мы разработчики, архитекторы, аналитики, но при этом мы делаем одно дело и любим его одинаково и идем в одном направлении, развиваемся и стремимся стать профессиональнее и опытнее. Мы работаем над множеством проектов и продуктов, которые нужны людям, каждый вносит свой вклад в общий успех нашей компании. Мы видим цель и идем к ней!
А еще мы просто хорошие, веселые, энергичные и умные люди! 

## Глоссарий

## Вводные
*Необходимо разработать сервис:*
1)	Сервис бесплатный, но должен быть доступен только абонентам МТС.
2)	Позволяющий отображать в приложении на мобильном телефоне шпаргалки в форматах pdf, txt, epub, которые пользователь может загрузить через приложение.
3)	Нужно проработать функционал работы сотрудников или привилегированных юзеров (Рабочее место модератора), которые будут загружать / категоризировать контент, а также функционал для интеграции с мобильным приложением и бэкендом.
4)	После накопления базы шпаргалок появилась потребность в построении системы хранения контента для размещения файлов и быстрого доступа к ним.  Для нас важно, чтобы контент предоставлялся только тем пользователям, которым выданы права на конкретный файл или группу файлов, а также чтобы данные, передаваемые по сети, были максимально защищены.
5)	Мы ожидаем большой рост популярности сервиса в связи с тем, что подготовка к экзаменам с репетиторами - это довольно дорогостоящий процесс, который могут позволить себе не более 10% населения. Ожидаемая нагрузка - 500 rps с пиками в 800 rps в периоды экзаменов.
6)	Нужен функционал по продаже «шпаргалок» одними пользователями другим пользователям с использованием единого платежного шлюза МТС Банка.

## Бизнес сценарии и цели
**Бизнес цели**
1)  Развивать список предоставляемых услуг в эко системе МТС.
2)  Задействовать интерес потребителей в обучении, необходимости иметь под рукой шпаргалку по нужной теме.
3)  Повышать узнаваемость бренда
4)  Расширение базы абонентов за счет привлечения дополнительных клиентов из-за бесплатного сервиса для заинтересованных клиентов в данном сервисе, но являющихся абонентами других операторов.

| #     | Описание                                                                                                                           |
|-------|------------------------------------------------------------------------------------------------------------------------------------|
| BR.01 | Нужен сервис, который позволит сохранять шпаргалки в виде коротких текстов и картинок.                                             |
| BR.02 | Давать возможность быстро загружать свои данные в различных форматах, который будет сразу же после проверки доступен               |
| BR.03 | Сервис должен ограничивать доступ к контенту. Пользователь может просматривать шпаргалки только получив права на конкретные данные |
| BR.04 | Сервис должен позволять  воспользоваться чужими данными купив их у другого пользователя                                            |
| BR.05 | Сервис должен давать возможность удобного поиска нужной информации                                                                 |
| BR.06 | Сервис должен обеспечивать работу модераторов                                                                                      |
| ----  | ---                                                                                                                                |

Предоставлять возможность иметь базу накопленных знаний в виде коротких текстов и картинок, то есть так называемых шпаргалок для подготовки к экзаменам, или использования в работе.

***Сценарии***

*Пользователь*

•   Регистрируется/ проходит авторизацию в системе/создает профиль
![](Сценарии/сценарии_использования-Регистрация_и_допродажа.jpg)

•   Производит загрузку шпаргалок

•   Ведет внутренний каталог для своих данных

•   Продает доступ к своим данным   

*Администратор/модератор*

•   При загрузке определяет качество контента, проводит модерацию

•   Ведет общий каталог тем и тегов•    

## Стейкхолдеры

## Границы

| # | Описание |
|----|----------|
| CNS-1 |          |

## Допущения

| # | Описание |
|----|-------------|
| ASM-1 |             |

## Требования к системе


### Функциональные требования

| #     | Cистема должна позволять                                                               |
|-------|----------------------------------------------------------------------------------------|
| FR.01 | пользователям регистрироваться и авторизовываться в системе                            |
| FR.02 | проверять является ли пользователь абонентом МТС                                       |
| FR.03 | администраторам заводить супервизоров                                                  |
| FR.04 | администраторам назначать модераторов                                                  |
| FR.05 | авторам загружать шпаргалки в систему                                                  |
| FR.06 | авторам настраивать уровни видимости для шпаргалок                                     |
| FR.07 | авторам группировать и тегировать шпаргалки                                            |
| FR.08 | авторам разрешать выбранным читателям просмотривать шпаргалки или группы шпаргалок;    |
| FR.09 | авторам удалять шпаргалки                                                              |
| FR.10 | читателям просматривать шпаргалки                                                      |
| FR.11 | читателям сохранять шпаргалки для просмотра в оффлайн режиме                           |
| FR.12 | читателям оставлять жалобу на шпаргалку                                                |
| FR.13 | модераторам и супервизорам разрешать или запрещать публикацию шпаргалки                |
| FR.14 | отбирать шпаргалки для просмотра супервизором по преднастроенному алгоритму            |
| FR.15 | модераторам просматривать шпаргалки не прошедшие модерацию                             |
| FR.16 | авторам назначать цену за доступ к шпаргалке/группе шпаргалок                          |
| FR.17 | читателям покупать доступ к шпаргалке/группе шпаргалок через единый платежный шлюз МТС |
| FR.18 | читателям просматривать шпаргалки,к которым был куплен доступ                          |
| FR.19 | администраторам настраивать справочники мета данных                                    |
| FR.20 | не абонентам МТС перенести свой номер оператору МТС                                    |
| ---   | ---                                                                                    |
  
### Атрибуты качества
| #     | Атрибут качества      | Обоснование                                                                                                                                                                     |
|-------|-----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| AR.01 | 	Масштабируемость     | 	Со временем объём хранимых в системе данных будет увеличиваться. Будет расти количество пользовательских данных и количество хранимых шпаргалок.                               |
| AR.02 | 	Эластичность         | 	В разные периоды времени количество пользователей, работающих с системой будет увеличиваться. Например, в периоды экзаменов нагрузка на систему увеличится более чем на 50%.   |
| AR.03 | 	Безопасность         | 	Основная идея бизнеса в платном предоставлении доступа к авторскому контенту. Поэтому данный атрибут качества является одним из приоритетных.                                  |
| AR.04 | 	Совместимость        | 	Система должна быть совместима с другими продуктами МТС: системой авторизации и платежным шлюзом.                                                                              |
| AR.05 | 	Устойчивость к сбоям | 	С системой взаимодействуют множество групп пользователей, преследующих свои цели. Проблема с одним из функциональных блоков не должны блокировать работу других пользователей. |



## Architecture Decision Records

| #      | Описание                                                                                                                                                                                                               |
|--------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ADR.01 | В проекте будем использовать практику ведения Architecture Decision Records                                                                                                                                            |
| ADR.02 | В качестве архитектурного стиля будет использоваться микросервисная архитектура. Подробнее в [ADR.02 Выбор архитектурного стиля](https://gitlab.services.mts.ru/avendour/archkata/-/blob/master/ADR/ADR02ArchStyle.md) |
| ADR.03 | В проекте будет использовтаься графовая система хранения данных для хранения информации о доступов к статьям.                                                                                                          |
| ADR.04 | В системе не будут храниться персональные данные клиентов. Все персональные данные будут хранится в других системах МТС, через которые будет происходить идентификация пользователя по номеру телефона                 |
| ADR.05 | 

## Архитектура

### Контекст системы
![](C4/ContextDiagram.png)
### Контейнерная диаграмма
![](C4/ContainerDiagram.png)
### Компонентная диаграмма Content
![](C4/ComponentDiagram.png)
