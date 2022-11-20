[![logo](https://github.com/ShchegolevYA/Incentivized-testnet/blob/main/Aleo/png/logo.png)](https://developer.aleo.org/)


<div style="text-align: center;">

[![Website](https://img.shields.io/badge/-Website-1A4468?style=for-the-badge&logo=Website&logoColor=27A0D9)]( https://www.aleo.org/)
[![GitHub](https://img.shields.io/badge/-GitHub-1A4468?style=for-the-badge&logo=GitHub&logoColor=12141D)](https://github.com/AleoHQ)
[![Twitter](https://img.shields.io/badge/-Twitter-1A4468?style=for-the-badge&logo=Twitter&logoColor=1C9DEB)](https://twitter.com/AleoHQ)
[![Community Twitter](https://img.shields.io/badge/-Community_Twitter-1A4468?style=for-the-badge&logo=Twitter&logoColor=1C9DEB)](https://twitter.com/aleocommunity)
[![LinkedIn](https://img.shields.io/badge/-LinkedIn-1A4468?style=for-the-badge&logo=linkedin&logoColor=007BB6)](https://www.linkedin.com/company/aleohq/)
[![YouTube](https://img.shields.io/badge/-YouTube-1A4468?style=for-the-badge&logo=YouTube&logoColor=FF0000)]( https://www.youtube.com/channel/UCS_HKT2heOC_q88YQLiJt0g)
[![Community_Forum](https://img.shields.io/badge/-Community_Forum-1A4468?style=for-the-badge&logo=Website&logoColor=27A0D9)](https://community.aleo.org/)
[![Community_Calendar](https://img.shields.io/badge/-Community_Calendar-1A4468?style=for-the-badge&logo=Website&logoColor=27A0D9)](https://www.aleo.org/community/calendar)
[![Developer_Documentation](https://img.shields.io/badge/-Developer_Documentation-1A4468?style=for-the-badge&logo=Website&logoColor=27A0D9)](https://developer.aleo.org/)
[![Community_Blog](https://img.shields.io/badge/-Community_Blog-1A4468?style=for-the-badge&logo=Website&logoColor=27A0D9)](https://medium.com/@AleoHQ)
[![Announcements_Blog](https://img.shields.io/badge/-Announcements_Blog-1A4468?style=for-the-badge&logo=Website&logoColor=27A0D9)](https://www.aleo.org/blog)


</div>

# 1. Описание
`Aleo` — это новый блокчейн `уровня 1`, который использует `криптографию с нулевым разглашением` для создания масштабируемых и частных децентрализованных приложений. В нашей архитектуре приложения не выполняются в цепочке; скорее, пользователи выполняют приложение вне сети и публикуют в цепочке `zkSNARK (короткие доказательства с нулевым разглашением)`, которые подтверждают правильность выполнения с сохранением конфиденциальности. Затем цепочка проверяет эти короткие доказательства во времени, `*независимом*` от времени работы приложения.

**snarkOS** — это децентрализованная операционная система для приложений с нулевым разглашением. Этот код формирует основу сети Aleo, которая проверяет транзакции и хранит приложения в зашифрованном состоянии общедоступным способом.

# 2. Руководство по установке
## 2.1 Требования к серверу
Ниже приведены минимальные требования для запуска узла Aleo:

[![logo](https://github.com/ShchegolevYA/Incentivized-testnet/blob/main/Aleo/png/Requirements.png)]

* CPU: 16-cores (32-cores preferred)
* RAM: 16GB of memory (32GB preferred)
* Storage: 128GB of disk space
* Network: 10 Mbps of upload and download bandwidth
  
Внимание! Для запуска проверочного узла (Aleo Prover), желательно преобретать конфигурацию, чем мощнее,тем лучше. Это позволит вам быть более конкурентноспособным в тестнете.

## Подготовка сервера
Обновление сервера
```
sudo apt update && sudo apt upgrade -y
```
Установка необходимых зависимостей
```
sudo apt install curl tar wget clang pkg-config libssl-dev jq build-essential git make ncdu net-tools -y
```


## 2.2 Установка
Устанавливаем Rust (версия Rust v1.64+)
```
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```
Клонируем репозиторий с Github:
```
git clone https://github.com/AleoHQ/snarkOS.git --depth 1
```
Переходим в директорию `snarkOS`:
```
cd snarkOS
```
**[Для пользователей Ubuntu]** Вспомогательный скрипт для установки зависимостей. (Запускаем из каталога `snarkOS`):
```
./build_ubuntu.sh
```
Устанвливаем `snarkOS`:
```
cargo install --path .
```
# 3. Запуск узла Aleo
## 3a. Запуск клиентского узла (Aleo Client)
Начните с пункта 2.2.

Запускаем клиентский узел из каталога `snarkOS`:
```
./run-client.sh
```
## 3b. Запуск проверочного узла (Aleo Prover)
Начните с пункта 2.2.

Создаем аккаунт Aleo (генерируем учетную запись):
```
snarkos account new
```
После, в терминале, отобразятся сгенерированные данные.

**Не забудьте сохранить приватный (Private Key) и публичный (View Key) ключи. ** Ниже приведен пример вывода в терминале:
```
Attention - Remember to store this account private key and view key.

  Private Key  APrivateKey1xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx  <-- Save Me And Use In The Next Step
     View Key  AViewKey1xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx  <-- Save Me
      Address  aleo1xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx  <-- Save Me
```      
Запускаем проверочный узел из каталога `snarkOS`:
  ```
  ./run-prover.sh
  ```
  При запросе введите ваш приватный ключ:
  ```
  Enter the Aleo Prover account private key:
APrivateKey1xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```
# 4. FAQs
## 1. Мой узел не может скомпилироваться.
* Убедитесь, что на вашем компьютере установлен `Rust v1.64+`. Команда по установке находится в пункте 2.2 или можно найти [здесь.](https://www.rust-lang.org/tools/install)
* Если во время компиляции появляются большие ошибки, попробуйте запустить `cargo clean`.
* Убедитесь `snarkOS` запущен с помощью `./run-client.sh` или `./run-prover.sh`.
## 2. Мой узел не может подключиться к пирам.

* Убедитесь, что порты `4133/tcp` и `3033/tcp` открыты на вашем маршрутизаторе и брандмауэре ОС.
* Убедитесь `snarkOS` запущен с помощью `./run-client.sh` или `./run-prover.sh`.

## 3. Не генерируется новый адрес
* Перед запуском (`snarkos account new`) выполнить команду `source ~/.bashrc`
* Также дважды проверьте написание слова `snarkos`. Обратите внимание, что каталог `/snarkOS`, а команда `snarkos`
  
# 5. Интерфейс командной строки
Чтобы запустить узел с пользовательскими настройками, обратитесь к полному списку опций и флагов, доступных в интерфейсе командной строки `snarkOS`.
Полный список флагов и опций CLI можно просмотреть с помощью `snarkos --help`:

```
snarkOS 
The Aleo Team <hello@aleo.org>

USAGE:
    snarkos [OPTIONS] <SUBCOMMAND>

OPTIONS:
    -h, --help                     Print help information
    -v, --verbosity <VERBOSITY>    Specify the verbosity [options: 0, 1, 2, 3] [default: 2]

SUBCOMMANDS:
    account    Commands to manage Aleo accounts
    clean      Cleans the snarkOS node storage
    help       Print this message or the help of the given subcommand(s)
    start      Starts the snarkOS node
    update     Update snarkOS
```

Ниже приведены параметры команды `snarkos start`:
```
snarkos-start 
Starts the snarkOS node

USAGE:
    snarkos start [OPTIONS]

OPTIONS:
        --beacon <BEACON>          Specify this as a beacon, with the given account private key for this node
        --client <CLIENT>          Specify this as a client, with an optional account private key for this node
        --connect <CONNECT>        Specify the IP address and port of a peer to connect to [default: ]
        --dev <DEV>                Enables development mode, specify a unique ID for this node
    -h, --help                     Print help information
        --logfile <LOGFILE>        Specify the path to the file where logs will be stored [default: /tmp/snarkos.log]
        --network <NETWORK>        Specify the network of this node [default: 3]
        --node <NODE>              Specify the IP address and port for the node server [default: 0.0.0.0:4133]
        --nodisplay                If the flag is set, the node will not render the display
        --norest                   If the flag is set, the node will not initialize the REST server
        --prover <PROVER>          Specify this as a prover, with the given account private key for this node
        --rest <REST>              Specify the IP address and port for the REST server [default: 0.0.0.0:3033]
        --validator <VALIDATOR>    Specify this as a validator, with the given account private key for this node
        --verbosity <VERBOSITY>    Specify the verbosity of the node [options: 0, 1, 2, 3] [default: 2]
```
 # 6. Режим разработки
 ## 6.1 Быстрый старт
 В первом терминале запустите маяк:
 ```
 cargo run --release -- start --nodisplay --dev 0 --beacon ""
 ```
 В втором терминале:
 ```
 cargo run --release -- start --nodisplay --dev 1 --prover ""
 ```
 Повторяйте данную команду необходимое количество раз.

 ## 6.2 Операции
 Важно инициализировать узлы, начиная с «0» и увеличивая на «1» для каждого нового узла.
  Ниже приведен список опций для инициализации узла (замените `XX` числом, начинающимся с `0`):
 ```
 cargo run --release -- start --nodisplay --dev XX --beacon ""
cargo run --release -- start --nodisplay --dev XX --validator ""
cargo run --release -- start --nodisplay --dev XX --prover ""
cargo run --release -- start --nodisplay --dev XX --client ""
cargo run --release -- start --nodisplay --dev XX
```
Если тип узла не указан, по умолчанию узел будет иметь значение `--client`.

**Очистить**

Чтобы очистить хранилище узла, выполните:
```
cargo run --release -- clean --dev XX
```
