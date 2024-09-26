# Mission 3

## Part 0

[Ссылка на базу данных]( https://supabase.com/dashboard/project/sahwximyzcsylxepdehs/editor/29133?schema=public)

## Part 1

[Ccылка на buildship](https://buildship.app/p/buildship-wsajnu/settings/general)

## Part 2

[Cсылка на видео]()

Запрос 1. Получить список юзернеймов пользователей
	SELECT username FROM users 

Запрос 2. Получить количество отправленных сообщений каждым пользователем
	SELECT u.username, COUNT(m.id) AS number_of_sent_messages
	FROM users u
	LEFT JOIN messages m ON u.id = m.from
	GROUP BY u.username;

Запрос 3. Получить пользователя с самым большим количеством полученных сообщений и само количество:
	SELECT u.username, COUNT(m.id) AS number_of_received_messages
	FROM users u
	LEFT JOIN messages m ON u.id = m."to"
	GROUP BY u.username
	ORDER BY number_of_received_messages DESС
	LIMIT 1;

Запрос 4. Получить среднее количество сообщений, отправленное каждым пользователем
	SELECT AVG(messages_sent) AS average_sent_messages
    FROM (
        SELECT COUNT(m.id) AS messages_sent
        FROM users u
        LEFT JOIN messages m ON u.id = m."from"
        GROUP BY u.id
    ) AS subquery;
