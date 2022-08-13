# Near-Stake-Wars-3-Guide
Процесс установки ноды Near в рамках Stake Wars 3

Цель данной статьи - описать процесс установки ноды, зафиксировать возникающие проблемы и пути их решения.

В процессе работы с данным проектом, вам могут пригодится следующие ссылки:

Репозиторий Near Stake Wars: https://github.com/near/stakewars-iii
Дискорд сервер для общения с коллегами: https://discord.gg/7TercRzRgA

Остальное можно будет найти в процессе изучения отчета. 

# Этап 0. Выбор сервера и создание кошельков

Изначально, были заявлены достаточно снисходительные требования к серверу: 

| Hardware       | Chunk-Only Producer  Specifications                                   |
| -------------- | ---------------------------------------------------------------       |
| CPU            | 4-Core CPU with AVX support                                           |
| RAM            | 8GB DDR4                                                              |
| Storage        | 500GB SSD                                                             |

Рекомендция уже устарела, на таком сервере поднять ноду не представляется возможным

Актуальные минимальные требования для работы: 

| Hardware       | Chunk-Only Producer  Specifications                                   |
| -------------- | ---------------------------------------------------------------       |
| CPU            | 6-Core CPU with AVX support                                      |
| RAM            | 16 GB DDR4 + 32 GB Swap file                                          |
| Storage        | 500GB SSD                                                             |

В процессе ресерча, оптимальным вариантом оказались сервера [Contabo](https://contabo.com/en/vps/)

Выбираем тариф с запасом от актуальных требований - CLOUD VPS L

![Screenshot_272](https://user-images.githubusercontent.com/107760840/184492578-84e0e72a-0950-4baf-a3b8-13d88d9d0a31.png)

Процесс регистрации и заказа сервера прозрачный, думаю описывать его не нужно. 
Единственное что, если вы из РФ, вам потребуется помощь с оплатой (BitFree, PayWithMoon) и пройти KYC.

# Создание кошелька

Переходим по ссылке https://wallet.shardnet.near.org/ и нажимаем Создать кошелек

![image](https://user-images.githubusercontent.com/107760840/184493096-e0eff491-40af-46c8-86fd-550b7f638370.png)

Далее жмем Reserve My Account ID, метод - Мненомическая фраза 

![image](https://user-images.githubusercontent.com/107760840/184493111-b674cc52-8267-451a-9cfd-624bcd9cd95b.png)

Далее жмем продолжить, и сохраняем нашу фразу в место, где вы ее не потеряете, после чего нажимаем кнопку Продолжить, нас попросит ввести одно из 12 слов

![image](https://user-images.githubusercontent.com/107760840/184493150-8d96d288-f9fa-43f6-9845-3377c59918e8.png)

В процессе завершения регистрации, возможно будут возникать ошибки как на скрине ниже 

![image](https://user-images.githubusercontent.com/107760840/184493198-c54e41f6-8dac-4c32-88a5-592709c96181.png)

Процесс нужно будет повторять до тех пор, пока вы не получите ДВА именных кошелька, после чего с одного нужно будет отправить монеты на другой и можно на этом закончить

![image](https://user-images.githubusercontent.com/107760840/184493318-67c2b5bb-ea89-4cfd-a38a-0fe6e1fbf232.png)

## Продолжение
[Установка Near-Cli](./01.md)







