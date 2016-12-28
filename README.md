# «Правильный» релиз

Т.к. в последние месяцы работы в компании, я занимался релизами почти всех веб-приложений, мне удалось найти, на мой взгляд, оптимальный подход к этому. Ниже я опишу и сам процесс подготовки и выкладки релиза, а также инструментарий, который необходим для этого.

## В общем

Итак, ваш менеджер проекта дает вам задачу подготвить новый релиз приложения. В свою очередь вам необходимо уточнить:

1. Куда выкладывать релиз — площадка dev, test, staging или prod? Конкретно, у «роботов», я не встречал, чтобы были все 4 площадки. Скорее всего есть 2 — dev(test) и staging. Но в идеале, должны быть все 4. Поэтому ниже я опишу, для чего каждая из них нужна:

  * **dev** – это песочница для разработчиков, хотя в случае веб-приложений она не очень нужна, т.к. веб-приложение, зачастую, можно целиком запустить локально;

  * **test** – сюда выкладывают сборки для тестирования; обычно это предрелизные сборки;

  * **staging** — площадка, которая по своей конфигурации максимально схожа с продакшеном, но при этом доступна только изнутри; используется для тестирования каких-либо опасных изменений в окружении максимально приближенном к боевому;

  * **prod** — он и в Африке прод — на нем должна крутиться последняя стабильная версия приложения и сюда же выкладываются hotfix'ы;

2. Какой номер версии приложения ставить? Это может быть важно, т.к. менеджер мог договориться с заказчиком о передаче конкретной версии приложения. В последнее время я старался следовать semver'у, хотя это не всегда получалось. Кратко о нем:

  1. Номер версии состоит из 3-х цифр, разделенных точками: X.Y.Z.

    * **X** – это мажорный релиз (т.е. изменение этой цифры говорит, о том, что вы релизите мажорную версию вашего прилоежения), который ломает или не совместим по API с предыдущей версией. К примеру, вы переписали роутинг приложения или полностью поменяли дизайн. Зачастую, мажорной версией становится версия с большим кол-вом новых фич.

    * **Y** — это минорный релиз — вы сделали изменения, но они обратно-совместимы с предыдущей версией. Обычно, это небольшое кол-во новых фич.
