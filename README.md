# Near-Stake-Wars-3-Guide
Процесс установки ноды Near в рамках Stake Wars 3

Цель данной статьи - описать процесс установки ноды, зафиксировать возникающие проблемы и пути их решения.

В процессе работы с данным проектом, вам могут пригодится следующие ссылки:

Репозиторий Near Stake Wars: https://github.com/near/stakewars-iii
Дискорд сервер для общения с коллегами: https://discord.gg/7TercRzRgA

Остальное можно будет найти в процессе изучения отчета. 

# Этап 1. Выбор сервера

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

# Этап 2. Создание кошелька

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

# Этап 2. Установка NEAR-CLI

В процессе работы, я буду использовать программу [MobaXTerm](https://download.mobatek.net/2212022060563542/MobaXterm_Portable_v22.1.zip)

Небольшое примечание, из соображений безопасности рекомендуется установить NEAR-CLI на компьютер, отличный от вашего узла валидатора, и чтобы на вашем узле валидатора не хранились ключи полного доступа. Но в рамках тестнета, это значения не имеет.

После того, как вы получили данные для доступа к серверу, вам необходимо подключится к нему.

Запускаем Moba, выбираем Session > SSH, заполняем как на картинке, только IP - вашего сервера, пароль берем из информации к серверу, вставляем кликнув в консольи правой кнопкой мыши и жмем Enter

![Screenshot_236](https://user-images.githubusercontent.com/107760840/184492844-814c73c5-f2ed-4962-b745-f39f6a847aee.png)

После успешного подключения мы видим следующее 

![image](https://user-images.githubusercontent.com/107760840/184492890-f7aeab44-160a-442c-9533-8d070afcfdf9.png)

Обновляемся следующей командой:

```
sudo apt update && sudo apt upgrade -y
```
![image](https://user-images.githubusercontent.com/107760840/184493616-268d8887-9dc6-4d0e-944f-07cfa4699492.png)

Готово.

![image](https://user-images.githubusercontent.com/107760840/184493633-86de89f8-e9fa-4a73-b142-5c2911204d52.png)


##### Устанвливаем тулзы для разработки, паралельно производим их настройку, я буду показывать команды и результат:
```
curl -sL https://deb.nodesource.com/setup_18.x | sudo -E bash -  
```
![image](https://user-images.githubusercontent.com/107760840/184493646-da295e63-4f81-4ecb-a100-fabf700282dd.png)

```
sudo apt install build-essential nodejs

В процессе, необходимо будет подтверждать некоторые запросы от системы, в данном случае буквой Y
```
![image](https://user-images.githubusercontent.com/107760840/184493662-2644125a-57cc-4f1f-ba81-69a70b0fa3f7.png)

```
PATH="$PATH"
```
![image](https://user-images.githubusercontent.com/107760840/184493707-6abc618e-9e0e-4143-9d9e-7d8dac00d456.png)

Проверяем версии тулз
```
node -v
```
```
npm -v
```

![image](https://user-images.githubusercontent.com/107760840/184493739-c9b34984-4248-41dd-82e9-ab3efc2b6f7b.png)

##### Установка NEAR-CLI

```
sudo npm install -g near-cli
```
![image](https://user-images.githubusercontent.com/107760840/184493816-46e01ca9-7bdb-4663-a9fb-67fb83c83200.png)

Производим следующие настройки:

```
export NEAR_ENV=shardnet
```
```
echo 'export NEAR_ENV=shardnet' >> ~/.bashrc
echo 'export NEAR_ENV=shardnet' >> ~/.bash_profile
source $HOME/.bash_profile
```
![image](https://user-images.githubusercontent.com/107760840/184493895-dbd22dce-057e-4635-9441-610e71d1fccd.png)

##### Проверяем встал ли NEAR-CLI

```
near proposals
```

![image](https://user-images.githubusercontent.com/107760840/184493913-cef02a01-d429-4b52-ac6b-60b658a96fbe.png)

![image](https://user-images.githubusercontent.com/107760840/184493924-bc102741-002b-412b-b778-620bc2307485.png)

На этом, установка Near-Cli завершена.

## Продолжение далее по ссылке

[Установка ноды](./002.md)







