### Разработка игр на Unreal Engine 5
# Документация к домашнему заданию
Работу выполнил студент БПИ225 Беренштейн Аркадий Игоревич

## Генерация комнат
Генерация происходит по следующему алгоритму:
1. Рандомайзером задаётся количество комнат в пределах от 6 до 10.
   
2. Создаётся начальная комната, где спавнится игрок. В ней нет ловушек и лечилок, только две двери.
   
3. В зависимости от того, какую дверь выберет игрок, происходит генерация следующей комнаты, а затем открывается дверь для игрока.
   
4. В базовой версии комнаты расположены точки спавна ловушек или предметов, на полу -- 17 точек спавна, на стене -- 16. На них случайным образом спавнятся ловушки.
   
5. После того, как игрок зашел в комнату, дверь за ним закрывается, и игрок уже не сможет её открыть.
    
6. После закрытия двери старая комната удаляется, а счетчик комнат уменьшается. Счётчик уменьшается только после удаления, чтобы игрок не смог открывать две двери сразу и таким образом уменьшать кол-во комнат для быстрого прохождения.
    
7. Так генерируется комната за комнатой до тех пор, пока счётчик не станет равным 0. Тогда создаётся последняя комната со статуей, к которой надо подойти и повзаимодействовать.

## Изменение уровня сложности
Общего увеличения сложности при прохождении нет. Есть два типа комнат -- лёгкие и сложные. Сложность их различается количеством ловушек.
- Для лёгкой комнаты спавнится 7 наземных ловушек, и 4 настенных.
  
- Для комнаты повышенной сложности спавнятся 12 наземных ловушек и 9 настенных, а также синее сердце, при контакте с которым восстанавливает здоровье игроку.

## Реализованные дополнения
- В качестве дополнения была реализована подсказка пользователю, на какую кнопку можно провзаимодействовать с предметом, будь то дверь или статуя в конце игры. 
Эта подсказка работает в определенном радиусе, и когда игрок его покидает, то подсказка пропадает. Также подсказка пропадает после взаимодействия с предметом.

- Было добавлено меню, появляющееся после смерти и победы персонажа. 
Игрок может выбрать, начать ли ему попытку заново или выйти из игры.

- После смерти модель персонажа падает на землю, и игрок не может больше им управлять.

- Также в игру добавлены текстуры, создающие атмосферу подземелья.

## Известные баги
- Пока дверь закрывается, можно успеть пролезть обратно. Тогда предыдущая комната уничтожится, а герой погибнет.

- Деспавнятся не все объекты предыдущей комнаты. Из-за этого может произойти коллизия, если на месте, где была комната, наложатся объекты другой.

## Ссылки на источники
- [Видео-урок на Ютубе по генерации подземелий](https://youtu.be/4ddbnQIuwAM?si=JPmlB9tXbivvgzu1)
  
Оттуда была взята общая концепция генерации комнат относительно выходов из них. 
Но для нашей задачи мне показалось, что лучше генерировать по одной комнате за раз, а старые удалять после закрытия двери. 
Тогда не возникнет коллизии, когда одна комната накладывается на другую.

- [Туториал по созданию летающих объектов](https://www.youtube.com/watch?v=s4YMltsdErc&ab_channel=RyanLaley)

Из этого урока была взята техника создания летающих объектов, в данном случае металлических шаров, наносящих урон игроку.
