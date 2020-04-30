---
layout: post
title:  Drupal7 записки
date:   2020-04-30 19:12:28 +0600
tag: server www
---

При переносе сайта долго не мог понять - почему не работает...
Оказалось права на файлы!

Забыл пароль от админки
[статья](https://drupal-admin.ru/blog/быстрый-сброс-пароля-админа-drupal)
из корня
$ ./scripts/password-hash.sh "1234"
и в базе
UPDATE users SET pass ='$S$D0vUizH2S/KoZkbj0u8c6eErm9xjWr1KtKBr94Q1UhsWYe.DimY9' WHERE name = 'admin';

Если "Аккаунт временно заблокирован по причине более чем 5 неудачных попыток входа."
[статья](https://mbaev.com/posts/kak-razblokirovat-akkaunt-posle-5-neudacnyh-popytok-vhoda)
в базе
delete from flood;

Пока все!!!