# Тестовое задание. iOS разработка.

Данный документ является тестовым заданием, предлагаемым к выполнению кандидатам на должность нативных iOS разработчиков. 

Философия нашей компании предполагает нетворкинг основанный на желании работников
- Квалификационно развиваться
- Проявлять живой, неподдельный интерес к своему профессиональному направлению

Данный фактор неизбежно оставляет несмываемый отпечаток на том как мы подходим к bootstrap’ингу и поддержке наших проектов, внося некоторые особенности в производственные решения и процессы происходящие на предприятии.

Нативная iOS разработка может быть топиком исключительно большого ряда дискуссий. Тем не менее, скоагулировав весь поток знаний и явлений непрерывно связанных с разработкой нативных приложений в конечный, четкий список требований к кандидатам, мы выясняем, что вне зависимости от практики работы в IT, от соискателя мы ждем 3 вещи:
1. English language on a level no less than A2/B1, sufficient for productively googling rather vividly varying questions about why things don’t work or either how things are supposed to work.
2. Асинхронное программирование, задачи на многопоточность, архитектура асинхронных stateless-систем.
3. Работа с UICollectionView/UITableView, архитектура view controller’ов с очень сложными, многослойными, вложенными моделями и несколькими UICollectionView одновременно.

Эти три вышеописанных фактора, по-нашему мнению и из нашей практики, составляют 70% от всего того чем мы вообще занимаемся на работе в процессе реализации наших проектов, остальные 30% - верстка в Interface Builder’е c Autolayout’ом (деятельность, которую мы не упоминаем отдельно т.к. это - само собой разумеющийся навык и практика в нашей области) и specific domain problems. 

Кандидат в процессе выполнения тестового задания может блеснуть, и ему это зачтется, следующими делами:
1. Организация life-cycle’ов объектов участвующих в композиции поведений связанных с UICollectionView, представление массивов данных, их маппинг, инкапсуляция, разделение логики fetch’инга и представления.
1. Работа с GCD.
1. Лаконичность пропагации событий, ошибок и данных из model layer’а.
1. Композиция множества UIView в кастомную UIView.
1. Дополнительные баллы за реактив.

Задание: сделать iOS приложение для лук-апа информации о номерах телефонов.
В приложении должно быть:

- Сцена ввода номера
 
    ![Dialer Scene Screenshot](/IMG_000.png?raw=true "Dialer Scene Screenshot")

    Не строит тратить время на визуальное представление, главное реализовать функционал. Где стоит placeholder “Enter a phone number” - UITextView. Кнопка слева - выбор кода страны. У ней title всегда отображает текущий выбранный код страны. Внизу кнопка Search.

- Сцена выбора кода страны

    ![Countries Scene Screenshot](/IMG_001.png?raw=true "Countries Scene Screenshot")

    UITableViewController, конечно, можно использовать, но мы будем благодарны, если нет. Как Вы могли понять из контекста, эта сцена появляется при нажатии на кнопку выбора кода страны. Датасет статичный, в .json’е, но лежит на ремоуте. Надо асинхронно стянуть, спарсить, и наполнить с него UITableView, и только потом показать контроллер. Если покажете на первом контроллере спиннер пока парсите датасет, это будет очень здорово.

- Сцена просмотра результатов

    ![Results Scene Screenshot](/IMG_002.png?raw=true "Results Scene Screenshot")

    Номер принесите с предыдущего контроллера. Также, принесите название страны, чтобы отобразить под номером. Кнопка Continue внизу возвращает назад, на набор номера. На дизайне нет UINavigationItem’а, но не заморачивайтесь. Фронтенд вы пишите под (пока еще, на сегодняшний момент) ненаписанное API которое от Вас примет стринг с валидированным номером телефона и эскейпящий callback (блок в Objective-C, функция в Swift) который возвращает void (на Swift - Void), принимает поинтер на NSArray с поинтерами на стринги (на Swift - опциональный [String]) и поинтер на NSError (на Swift - опциональный Error). В центре будет UITableView с cell’ами в которых только один UILabel, в который Вам нужно отмапить один к одному результаты из callback’а. Покажете спиннер - здорово. Не покажете контроллер пока не отработает callback - тоже классно. Если callback сработал с ошибкой - покажите alert с localizedDescription’ом, вернитесь на экран с набором номера. Оформите API в протокол и придумаете его life-cycle - тоже будет очень здорово.

В условиях сжатых сроков соискатель должен понять, что в первую очередь будут смотреть и разбирать его код, структуру классов, алгоритмы, а также то, что это тестовое задание для вакансии iOS разработчика. Поэтому соискатель должен поставить приоритет на разработке под iOS.

Ах да, ссылка на .json со странами и кодами: 

https://raw.githubusercontent.com/isaac-weisberg/idsi-ios-development-test-task/master/com.idsiapps.whodatboi.dataset.countries.json

Also, one might `git checkout 0.1`