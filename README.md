# Домашнее задание к занятию 10.1 «Keepalived/vrrp» - Куприянов Владимир

### Инструкция по выполнению домашнего задания

1. Сделайте fork [репозитория c Шаблоном решения](https://github.com/netology-code/sys-pattern-homework) к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/gitlab-hw или https://github.com/имя-вашего-репозитория/8-03-hw).
2. Выполните клонирование данного репозитория к себе на ПК с помощью команды `git clone`.
3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
   - впишите вверху название занятия и вашу фамилию и имя
   - в каждом задании добавьте решение в требуемом виде (текст/код/скриншоты/ссылка)
   - для корректного добавления скриншотов воспользуйтесь инструкцией ["Как вставить скриншот в шаблон с решением"](https://github.com/netology-code/sys-pattern-homework/blob/main/screen-instruction.md)
   - при оформлении используйте возможности языка разметки md (коротко об этом можно посмотреть в [инструкции по MarkDown](https://github.com/netology-code/sys-pattern-homework/blob/main/md-instruction.md))
4. После завершения работы над домашним заданием сделайте коммит (`git commit -m "comment"`) и отправьте его на Github (`git push origin`);
5. Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
6. Любые вопросы по выполнению заданий спрашивайте в чате учебной группы и/или в разделе “Вопросы по заданию” в личном кабинете.

Желаем успехов в выполнении домашнего задания!

---

### Задание 1

Разверните топологию из лекции и выполните установку и настройку сервиса Keepalived. 

```
vrrp_instance test {

state "name_mode"

interface "name_interface"

virtual_router_id "number id"

priority "number priority"

advert_int "number advert"

authentication {

auth_type "auth type"

auth_pass "password"

}

unicast_peer {

"ip address host"

}

virtual_ipaddress {

"ip address host" dev "interface" label "interface":vip

}

}

```

*Пришлите скриншот рабочей конфигурации и состояния сервиса для каждого нода.*

MASTER нода:

![image](https://user-images.githubusercontent.com/124167007/227818329-123797af-9940-4958-b88d-775a927c52a2.png)
![image](https://user-images.githubusercontent.com/124167007/227818130-2cd3ff63-2dd8-4328-ab0e-f0f805b21cfc.png)
![image](https://user-images.githubusercontent.com/124167007/227818170-0375d320-3fad-4155-8703-80f0047eefd3.png)

SLAVE нода:

![image](https://user-images.githubusercontent.com/124167007/227818348-435c812e-63e2-44da-9ab3-d99dc9561414.png)
![image](https://user-images.githubusercontent.com/124167007/227818370-8c2e1cfe-9765-4abb-83db-59d2f0028a40.png)
![image](https://user-images.githubusercontent.com/124167007/227818383-de9817df-dece-4ad6-8625-0feee8df831b.png)

## Дополнительные задания со звёздочкой*

Эти задания дополнительные. Их можно не выполнять. На зачёт это не повлияет. Вы можете их выполнить, если хотите глубже разобраться в материале.
 
### Задание 2*

Проведите тестирование работы ноды, когда один из интерфейсов выключен. Для этого:
- добавьте ещё одну виртуальную машину и включите её в сеть;
- на машине установите Wireshark и запустите процесс прослеживания интерфейса;
- запустите процесс ping на виртуальный хост;
- выключите интерфейс на одной ноде (мастер), остановите Wireshark;
- найдите пакеты ICMP, в которых будет отображён процесс изменения MAC-адреса одной ноды на другой. 

 *Пришлите скриншот до и после выключения интерфейса из Wireshark.*
