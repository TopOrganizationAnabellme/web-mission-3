# Mission 3

## Part 0

[Ссылка на базу данных]( https://supabase.com/dashboard/project/sahwximyzcsylxepdehs/editor/29133?schema=public)

## Part 1

[Ccылка на buildship](https://buildship.app/p/buildship-wsajnu/settings/general)

## Part 2

[Cсылка на видео](https://drive.google.com/file/d/10U_k07riA69WynqAkTCM1bJutE0utNo_/view?usp=share_link)

Запрос 1. Получить список юзернеймов пользователей
	
	SELECT username FROM users

Запрос 2. Получить количество отправленных сообщений каждым пользователем
	
	SELECT u.username, COUNT(m.id) AS number_of_sent_messages
	FROM users u
	LEFT JOIN messages m ON u.id = m.from
	GROUP BY u.username;

Запрос 3. Получить пользователя с самым большим количеством полученных сообщений и само количество:
	
	SELECT username, COUNT(*) AS "number of received messages"
	FROM messages
	JOIN users ON messages.to = users.id
	GROUP BY username
	ORDER BY COUNT(*) DESC
	LIMIT 1;


Запрос 4. Получить среднее количество сообщений, отправленное каждым пользователем
	
	SELECT username, AVG(cnt) AS "average number of sent messages"
	FROM(
	SELECT messages.from, COUNT(*) AS cnt
	FROM messages
	GROUP BY messages.from
	) AS message_count
	JOIN users ON message_count.from = users.id
	GROUP BY username;

