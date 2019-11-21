# Добавление каналов и чатов в группу

**Акторы:** 

- Пользователь
- Приложение
- Бекенд
- База данных

**Цель:** Пользователь добавляет каналы и чаты в группу, чтобы вынести их на отдельную вкладку.

**Предусловия:** У пользователя есть аккаунт в приложении, пользователь зашел в приложение, у пользователя больше одного чата и/или канала, есть минимум одна группа, открыта вкладка нужной группы.

**Сценарий:**

1. Пользователь выбирает действие "Добавить в группу".

Если пользователь хочет создать новую группу, а не добавить чат(ы) и/или канал(ы) в уже существующую группу, то должен выполняться сценарий [Группировка каналов и чатов].

2. Приложение показывает список всех чатов и каналов.
3. Пользователь выбирает нужные чаты и каналы.
4. Приложение отмечает выбранные чаты и каналы.
5. Приложение отправляет бекенду информацию о добавлении чатов и/или каналов в группу:

    `/user/group/add?join=[chat1,chat2,channel1,..]&id=groupId`.

6. Бекенд отправляет запрос к базе данных для добавления чатов и каналов в группу.

    {Успешное добавление данных в базу}

7. Бекенд отправляет интерфейсу сообщение о успешном добвлении данных чатов и каналов в данные группы.
8. Приложение открывает вкладку группы с добавленными чатами и каналами.

**Результат:**

- Открывается вкладка группы.
- В группе появляется информация о добавленных чатах и каналах.
- У добавленных чатов и каналов появляется информация о группе.
- В базе данных добавлены новые чаты и каналы к группе.

**Исключения:**

3а. Пользователь не выбрал ни одного чата или канала.
4а. Выбранный чат или канал уже входит в какую-то группу.
7а. Бекенд возвращает 500.