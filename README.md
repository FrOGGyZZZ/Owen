Owen kilnController
==============

Turns a Orange Pi into a cheap, universal & web-enabled kiln Controller.
Forked from the reflow oven project: [picoReflow](https://apollo.open-resource.org/mission:resources:picoreflow)

Мне нужен был тонконастраиваемый контроллер печи для обжига, и как всегда за минимум $.

Этот проект является форком picoReflow форка kilnController от уважаемого botheredbybees.

Немного поправил вэб-морду (убрал ненужный функционал, ошибки и добалил немного отсебятины), немного руссифицировал, немного подретушировал CSS, взял основу драйвера MAX31856 и запилил его под этот проект(рабочего драйвера не нашёл, только наброски), так как мне нужна термопара тип-S.

## Железо

  * [OrangePI LITE2](https://aliexpress.ru/item/Sample-Test-Orange-Pi-Lite2-Single-Board-Discount-Price-for-Only-1pcs-Each-Order/32849206150.html) - Куплен по распродаже порядка 1650рэ с доставкой
  * [MAX 31856](https://aliexpress.ru/item/MAX31856-CJMCU-thermocouple-module-high-precision-development-board-A-D-converter-universal-type/32788292007.html) - Вышел порядка 750рэ
  * [S-Type Thermocouple Sensor](https://aliexpress.ru/item/High-Temperature-K-Type-S-type-Thermocouple-Sensor-for-Ceramic-Kiln-Furnace-2372-Fahrenheit-1300-Degree/32967487103.html) - Термопара 0°C to 1600°C
  * Solid State Relay Module [SSR-40DA](https://aliexpress.ru/item/solid-state-relay-SSR-10DA-SSR-25DA-SSR-40DA-10A-25A-40A-actually-3-32V-DC/32706812752.html) - Собственно твердотельное реле 40A/250V 3-32V DC Input 24-380VAC Output

### Подключение
​MAX31856 to OPi PIN 

 * 3V to Pin 17 
 * GND to Pin 14 
 * DO to Pin 16 
 * DI to Pin 18 
 * CS to Pin 10 
 * CLK to Pin 12

 * реле на 25 и 26 пины

## Установка

### Dependencies

External dependencies have been kept to a minimum to make it easily
deployable on any flavor of open-source operating system. 

#### Currently tested versions

  * greenlet-0.4.2
  * bottle-0.12.4
  * gevent-1.0
  * gevent-websocket-0.9.3

#### Ubuntu/Raspbian

    $ sudo apt-get install python3-pip python3-dev libevent-dev
    $ sudo pip3 install ez-setup
    $ sudo pip3 install greenlet bottle gevent gevent-websocket

#### Gentoo

    $ emerge -av dev-libs/libevent dev-python/pip3
    $ pip3 install ez-setup
    $ pip3 install greenlet bottle gevent gevent-websocket

#### Orange PI deployment

If you want to deploy the code on a PI for production:

    $ git clone https://github.com/Pako2/OrangePi.GPIO.git
    $ cd /OrangePi.GPIO
    $ sudo python3 setup.py install 
    $ OR (for H6 boards Lite2, One Plus and "3"): 
    $ sudo python3 setup.py install --force-h6


If you also want to use the in-kernel SPI drivers with a MAX31855 sensor:

    $ sudo pip3 install Adafruit-MAX31855

### Clone repo

    $ git clone https://github.com/FrOGGyZZZ/Owen.git
    $ cd Owen

## Configuration

Все параметры находятся в config.py. Скопируруйте config.py.EXAMPLE как config.py и отредактируйте.
Однако в lib/ в нужном драйвере необходимо задать модель BOARD для OPi.GPIO: 

  * OPi Zero (as ZERO) 
  * OPi Zero Plus (as ZEROPLUS) 
  * OPi Zero Plus2 H3 (as ZEROPLUS2H3) 
  * OPi Zero Plus2 H5 (as ZEROPLUS2H5)
  * OPi R1
  * OPi PC & PC Plus (as PCPCPLUS)
  * OPi One (as ONE)
  * OPi Lite (as LITE)
  * OPi PC2
  * OPi Prime (as PRIME)
  * OPi Lite2 (as LITE2)
  * OPi One Plus (as ONEPLUS)
  * OPi 3 (as THREE)

## Usage

### Server Startup

    $ cd Owen
    $ python3 owen.py

### Autostart Server onBoot
Как вариант. 

If you want the server to autostart on boot, run:

    sudo nano /etc/rc.local

add the line:

    `sudo python3 /You PATH to program/owen.py &`

### Client Access

Open Browser and goto http://IP-адрес:8080 (for local development) or the IP
of your PI and the port defined in config.py (default 8080).

### Build Instructions

Можете прочитать https://www.instructables.com/id/Build-a-Web-Enabled-High-Temperature-Kiln-Controll

## License

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.

## picoReflow

Для большего понимания смотрите picoReflow: https://apollo.open-resource.org/mission:resources:picoreflow
