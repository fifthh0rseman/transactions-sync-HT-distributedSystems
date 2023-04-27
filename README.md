# Часть 2: синхронизация на уровне базы данных

## Описание

Вам предоставлен класс DbSynchronizedAccounts, который содержит метод перевода денежных средств между банковскими
счетами. Информация об аккаунтах хранится в базе данных, доступ к которой обеспечивается через AccountRepository,
использующий Spring Data Jpa.
Необходимо обеспечить корректную работу данного метода в многопоточной среде с помощью механизмов синхронизации базы
данных.

## Мотивация

Нагрузка на приложение AppSynchronizedAccounts (из первой части задания) растет: необходимо обрабатывать большее
количество транзакций, в связи с чем хранение информации об аккаунтах в оперативной памяти мешает масштабированию
приложения, также существуют риски потери данных при перезагрузке сервиса. Поэтому в качестве хранилища информации об
аккаунтах была выбрана реляционная база данных.

## Задача

Необходимо обеспечить корректную работу DbSynchronizedAccounts с помощью трех механизмов синхронизации: 
пессимистической блокировки, оптимистической блокировки и уровня изоляции транзакций. Как и в предыдущем задании, необходимо
учесть возможность возникновения deadlock.

Вы можете протестировать свое решение с помощью класса DbSynchronizedAccountsTest.

## Отправка задания

Каждую реализацию выполняйте в отдельной ветке:

- реализация с пессимистической блокировкой - task_2_pessimistic;
- реализация с оптимистической блокировкой - task_2_optimistic;
- реализация с уровнем изоляции - task_2_isolation.

Для каждой реализации создайте отдельный pull request, например, из ветки с решением task_2_isolation_solving в
task_2_isolation по аналогии с предыдущим заданием.

## Ресурсы

- [ACID](https://ru.wikipedia.org/wiki/ACID)
- [Уровни изолированности транзакций](https://ru.wikipedia.org/wiki/Уровень_изолированности_транзакций)
- [Блокировки в БД](https://uthark.github.io/2009/04/22/blog-post_22/)
- [Оптимистичная блокировка](https://blog.mimacom.com/testing-optimistic-locking-handling-spring-boot-jpa/)
- [Пессимистичная блокировка](https://blog.mimacom.com/handling-pessimistic-locking-jpa-oracle-mysql-postgresql-derbi-h2/)
- [Spring Retry](https://www.baeldung.com/spring-retry)
- [Spring Transaction](https://www.baeldung.com/transaction-configuration-with-jpa-and-spring)
