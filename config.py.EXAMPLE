import logging

########################################################################
#
#   General options

### Logging
log_level = logging.INFO
log_format = '%(asctime)s %(levelname)s %(name)s: %(message)s'

### Server
listening_ip = "0.0.0.0"
listening_port = 8080

### Cost Estimate
kwh_rate        = 3.40  # Значение кВт\ч, нужно для расчёта потраченной электроэнергии
currency_type   = "RUB"   # Символ валюты позазываемый в расчёте

########################################################################
#
#   GPIO Setup (Your SoC Numbering Schema)
#
#   Check the *Pi docs to see where these GPIOs are
#   connected on the P1 header for your board type/rev.

### Outputs
gpio_heat = 26  # ПИН управления SSR (твердотельным реле) нагревателя
# Я не использую следующие 2 параметра, но на будущее или если кому надо:
gpio_cool = 22  # Регулирует ШИМ\PWM для вентилятора 12Вольт постоянного тока
gpio_air  = 8   # ПИН управления реле для вентилятора или задвижки поддувала

heater_invert = 0 # Управление инверсией реле нагревателя. Для постоянно замкнутого реле = 1

### Inputs
gpio_door = 11 # еще один параметр, который я не использую, но однажды может оказаться полезным

### Тип адаптера термрпары \ Thermocouple Adapter selection:
#   max31855 - bitbang SPI interface - Tuckie Lib
#   max31855spi - kernel SPI interface - Adafruit Blinka
#   max6675 - bitbang SPI interface - Tuckie Lib
max31855 = 0
max6675 = 0
max31855spi = 0 # if you use this one, you MUST reassign the default GPIO pins
max31856 = 1
max31856_termocouple_type = "s" # Тип термопары для MAX31856 (s,k,j)
### Thermocouple Connection (using bitbang interfaces)
gpio_sensor_cs = 10 # CS он же chip select, здесь любой пин
gpio_sensor_clock = 12 # CLK SCLK для не ядерного драйвера любой пин
gpio_sensor_data = 18 # DO MOSI для не ядерного драйвера любой пин
gpio_sensor_data_i = 16 # DI MISO для не ядерного драйвера любой пин

### Thermocouple SPI Connection (using adafrut drivers + kernel SPI interface)
spi_sensor_chip_id = 0 # Используется если ядерный драйвер

### amount of time, in seconds, to wait between reads of the thermocouple
sensor_time_wait = 0.5 # время опроса датчика температуры
# was .5 for solder reflow


########################################################################
#
#   PID parameters

pid_ki = 0.1  # Integration
pid_kd = 0.4  # Derivative
pid_kp = 0.5  # Proportional


########################################################################
#
#   Simulation parameters

sim_t_env      = 25.0   # deg C
sim_c_heat     = 100.0  # J/K  heat capacity of heat element
sim_c_oven     = 2000.0 # J/K  heat capacity of oven
sim_p_heat     = 2000.0 # W    heating power of oven
sim_R_o_nocool = 1.0    # K/W  thermal resistance oven -> environment
sim_R_o_cool   = 0.05   # K/W  " with cooling
sim_R_ho_noair = 0.1    # K/W  thermal resistance heat element -> oven
sim_R_ho_air   = 0.05   # K/W  " with internal air circulation


########################################################################
#
#   Time and Temperature parameters

temp_scale          = "c" # c = Celsius | f = Fahrenheit - Temperature inits used by thermocouple 
time_scale_slope    = "m" # s = Seconds | m = Minutes | h = Hours - Slope displayed in temp_scale per time_scale_slope
time_scale_profile  = "m" # s = Seconds | m = Minutes | h = Hours - Enter and view target time in time_scale_profile

