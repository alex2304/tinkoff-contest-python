# Trade Dealer for the Tinkoff API contest

![Overview of the system components](https://i.ibb.co/2d35vfQ/Untitled-Diagram-8-drawio.png)

Торговая система с подключаемыми стратегиями. 

Решение о торговле принимает стратегия. Всю остальную работу берет на себя система.

Сосредоточьтесь на описании и тестировании стратегий, не отвлекаясь на детали работы с API.

## Подготовка к работе
Для работы вам понадобится версия python 3.7+.

Установите зависимости (unix/macOS):
```bash
# create virtualenv locally
python3 -m venv ./venv
source venv/bin/activate
# install required dependencies
pip install -r requirements.txt
```

## Запуск трейдера
### Установка токена доступа
Для торговли нужен access token с уровнем доступа FULL ACCESS. Для торговли в песочнице нужен специальный sandobx token.

Перейдите на сайт Tinkoff и создайте токены [в разделе настройки](https://www.tinkoff.ru/invest/settings/).

Затем установите токены в переменные окружения:
```bash
# create the `example.env` file with the environment variables
cat > example.env << EOL
# tinkoff API token with the FULL_ACCESS level
INVEST_TOKEN=
# tinkoff API sandbox token
SANDBOX_TOKEN=
# (optional) if you have multiple accounts -- please, specify ID of the account you want to trade on
ACCOUNT_ID=
# (optional) you can track the orders made by the bot with this name
APP_NAME=
EOL
# add to the file required values in your favorite editor (I use Sublime Text here)
subl example.env
# source the file to load the env variables
source example.env
```

### Выбор и настройка стратегии

Система построена в соответствии с принципом [Dependency Inversion](https://habr.com/ru/company/productivity_inside/blog/505430/).
Конкретная стратегия не является частью системы -- бот может торговать по любой стратегии, которую ему укажут. 

Примеры стратегий хранится в папке `traders/`. Но благодаря единому интерфейсу, это может быть как локальный код, так и отдельный веб-сервер на другом хосте.

Чтобы начать торговлю по стратегии RSI, используя конфигурацию из файла `config/rsi_trader.yaml`:
```bash
python run_trader.py rsi -c config/rsi_trader.yaml
```

## Отладка стратегий

TODO:

## Обработка ошибок

TODO:

