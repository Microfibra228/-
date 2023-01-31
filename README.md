# -
Игра использующая ООП. Игра про известную вселенную трансформеров.

from random import *

autobot_name = ['Оптимус Прайм', 'Роллер', 'Джаз', 'Айронхайд', 'Рэтчет', 'Проул', 'Блустрик', 'Сайдсвайп',
                'Санстрикер', 'Уилджек', 'Трейлбрейкер', 'Хаунд', 'Мираж', 'Хоулер', 'Бамблби']        # Имена автоботов
decepticon_name = ['Мегатрон', 'Старскрим', 'Саундвейв', 'Мэйкшифт', 'Брейкдаун', 'Дредвинг', 'Вехикон', 'Чопшоп',
                   'Клипшэйд', 'Андербайт', 'Слипстрим']                                            # Имена дисептиконов
player_transformer = None
characteristic = ['power', 'health', 'armor', 'speed']


# Это чтоб всё ЧЁТКО выводилось! Для десептиконов и автоботов

def print_info_dexepticon(transformer):
    print('Его имя:', transformer.name, 'Поколение трансформера:', transformer.gen)
    print()
    print('Сила десептикона: ', transformer.power)
    print('Уровень здоровья десептикона: ', transformer.health)
    print('Уровень брони десептикона: ', transformer.armor)
    print('Скорость десептикона: ', transformer.speed)
    print()

    # Это чтоб всё ЧЁТКО выводилось! Для автоботов


def print_info_autobot(transformer):
    print('Имя трансформера:', transformer.name, 'Поколение трансформера:', transformer.gen)
    print()
    print('Сила трансформера: ', transformer.power)
    print('Уровень здоровья трансформера: ', transformer.health)
    print('Уровень брони трансформера: ', transformer.armor)
    print('Скорость трансформера: ', transformer.speed)
    print()


class Transformers:

    def __init__(self, power, health, armor, speed, gen, name, powerful):
        self.power = power         # Поле - сила
        self.health = health       # Поле - здоровье
        self.armor = armor         # Поле - броня
        self.speed = speed         # Поле - скорость
        self.gen = gen             # Поле - поколение (для разнообразия, потом от генов будут зависить характеристики)
        self.name = name           # Поле - имя (рандомно выбирается из второй строки)
        self.powerful = powerful   # Поле - Мощность (скрытое поле, сумма всех полей. Используется для вычисления побед)


# Создание трёх автоботов, что-бы в дальнейшем дать игроку выбрать своего трансформера
autobot1 = Transformers(randint(50, 100), randint(200, 350), randint(100, 150), randint(200, 300), randint(1, 9),
                        choice(autobot_name), 0)
autobot2 = Transformers(randint(200, 325), randint(100, 350), randint(105, 150), randint(90, 200), randint(1, 9),
                        choice(autobot_name), 0)
autobot3 = Transformers(randint(100, 250), randint(200, 250), randint(100, 250), randint(100, 300), randint(1, 9),
                        choice(autobot_name), 0)

# Присвоение значения полю powerful (строка 15)
autobot1.powerful = autobot1.power + autobot1.health + autobot1.armor + autobot1.speed
autobot2.powerful = autobot2.power + autobot2.health + autobot2.armor + autobot2.speed
autobot3.powerful = autobot3.power + autobot3.health + autobot3.armor + autobot3.speed

# Создание 5 противников/десептиконы, которые нужны в игровом цикле
deception1 = Transformers(randint(100, 200), randint(100, 200), randint(100, 200), randint(100, 200), randint(1, 9),
                          choice(decepticon_name), 0)
deception2 = Transformers(randint(100, 200), randint(100, 200), randint(100, 200), randint(100, 200), randint(1, 9),
                          choice(decepticon_name), 0)
deception3 = Transformers(randint(100, 200), randint(100, 200), randint(100, 200), randint(100, 200), randint(1, 9),
                          choice(decepticon_name), 0)
deception4 = Transformers(randint(100, 200), randint(100, 200), randint(100, 200), randint(100, 200), randint(1, 9),
                          choice(decepticon_name), 0)
deception5 = Transformers(randint(100, 200), randint(100, 100), randint(100, 200), randint(100, 300), randint(1, 9),
                          choice(decepticon_name), 0)

# Присвоение значения полю powerful (строка 15)
deception1.powerful = deception1.power + deception1.health + deception1.armor + deception1.speed
deception2.powerful = deception2.power + deception2.health + deception2.armor + deception2.speed
deception3.powerful = deception3.power + deception3.health + deception3.armor + deception3.speed
deception4.powerful = deception4.power + deception4.health + deception4.armor + deception4.speed
deception5.powerful = deception5.power + deception5.health + deception5.armor + deception5.speed

# Ввывод текста для начала игры
print()
print('Здравствуй, игрок. Все автоботы ждут тебя. Тебе стоит только сказать и начнётся решающий бой \n'
      'между трансформерами. Это наша последняя надежда, либо мы победим, либо они. \n'
      'Насколько нам известо Мегатрон применил на себе равалюционное оружие и превратил себя в нечто.\n'
      'Толко штурм их базы принесёт победу!')
start = input('Начнём битву?    ')
start.lower()

if start == 'да':
    print()
    print('Игрок, для сражения тебе понадобиться тело автобота.\n'
          'К сожалению у нас есть только три тела, которые мы можем востановить. Выбор за тобой!')
    # Предоставление выбора автобота игроку
    print()
    print('Вот первое тело:')
    print_info_autobot(autobot1)
    print()
    print('Вот второе тело:')
    print_info_autobot(autobot2)
    print()
    print('Вот третье тело:')
    print_info_autobot(autobot3)
    print()
    print()
    player_choice = input('Что выбираешь? ')

# Три сюжета игры (если игрок выбрал тело 1, 2 или 3)
    if player_choice == '1':
        print('Отлично', autobot1.name, 'был доблесным воином!')
        print()
        print('Автоботы, К БОЮ!')
        print()

        game_ok = True  # Эта переменная служит для понимания не закончился ли игравой цикл
        decepticon_num = 1  # Эта переменная служит для понимания какой по счёту сейчас враг
        deception = None  # Эта переменная служит для упрощения кода ей присваиватся определённый десептикон

        # Начало игрового цикла
        while game_ok:
            print('Твой враг уже приближается!')
            print('*сейчас тебе покажут случайную характеристику врага, по ней тебе нужно решить. Сражаться или '
                  'отступить!')
            print()
            if decepticon_num == 1:
                # Вывод случайной характеристики
                data_ch = choice(characteristic)
                if data_ch == 'power':
                    print('Сила десептикона:', deception1.power)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot1.powerful < deception1.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot1.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot1.powerful += 90
                if data_ch == 'health':
                    print('Уровень здоровья десептикона:', deception1.health)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot1.powerful < deception1.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot1.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot1.powerful += 90
                if data_ch == 'armor':
                    print('Уровень брони десептикона:', deception1.armor)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot1.powerful < deception1.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot1.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot1.powerful += 90
                if data_ch == 'speed':
                    print('Скорость десептикона:', deception1.speed)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot1.powerful < deception1.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot1.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot1.powerful += 90
                decepticon_num += 1

            if decepticon_num == 2:
                # Вывод случайной характеристики
                data_ch = choice(characteristic)
                if data_ch == 'power':
                    print('Сила десептикона:', deception2.power)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot1.powerful < deception2.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot1.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot1.powerful += 90
                if data_ch == 'health':
                    print('Уровень здоровья десептикона:', deception2.health)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot1.powerful < deception2.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot1.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot1.powerful += 90
                if data_ch == 'armor':
                    print('Уровень брони десептикона:', deception2.armor)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot1.powerful < deception2.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot1.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot1.powerful += 90
                if data_ch == 'speed':
                    print('Скорость десептикона:', deception2.speed)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot1.powerful < deception2.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot1.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot1.powerful += 90
                decepticon_num += 1

            if decepticon_num == 3:
                data_ch = choice(characteristic)
                if data_ch == 'power':
                    print('Сила десептикона:', deception3.power)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot1.powerful < deception3.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot1.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot1.powerful += 90
                if data_ch == 'health':
                    print('Уровень здоровья десептикона:', deception3.health)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot1.powerful < deception3.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot1.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot1.powerful += 90
                if data_ch == 'armor':
                    print('Уровень брони десептикона:', deception3.armor)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot1.powerful < deception3.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot1.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot1.powerful += 90
                if data_ch == 'speed':
                    print('Скорость десептикона:', deception3.speed)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot1.powerful < deception3.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot1.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot1.powerful += 90
                decepticon_num += 1

            if decepticon_num == 4:
                data_ch = choice(characteristic)
                if data_ch == 'power':
                    print('Сила десептикона:', deception4.power)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot1.powerful < deception4.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot1.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot1.powerful += 90
                if data_ch == 'health':
                    print('Уровень здоровья десептикона:', deception4.health)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot1.powerful < deception4.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot1.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot1.powerful += 90
                if data_ch == 'armor':
                    print('Уровень брони десептикона:', deception4.armor)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot1.powerful < deception4.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot1.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot1.powerful += 90
                if data_ch == 'speed':
                    print('Скорость десептикона:', deception4.speed)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot1.powerful < deception4.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot1.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot1.powerful += 90
                decepticon_num += 1

            if decepticon_num == 5:
                data_ch = choice(characteristic)
                if data_ch == 'power':
                    print('Сила десептикона:', deception5.power)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot1.powerful < deception5.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot1.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot1.powerful += 90
                if data_ch == 'health':
                    print('Уровень здоровья десептикона:', deception5.health)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot1.powerful < deception5.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot1.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot1.powerful += 90
                if data_ch == 'armor':
                    print('Уровень брони десептикона:', deception5.armor)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot1.powerful < deception5.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot1.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot1.powerful += 90
                if data_ch == 'speed':
                    print('Скорость десептикона:', deception5.speed)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot1.powerful < deception5.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot1.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot1.powerful += 90
                game_ok = False
        # все условные операторы выше ОДИНАКОВЫЕ

        #
        print()
        print('Не может быть! Нам удалось прорваться сквозь полчища десептиконов. Мегатрон уже близко.')
        print('Тебе нужно лишь тянуть время, пока мы отключаем его от этого оружия. Запомни!')
        print('Он слишком силён и не предсказуем. Бей и парируй! Удачи!')
        print()
        print('МЕГАТРОН: Что. Кто это? Ха. Жалкий автобот. Ты правда думаешь, что сможешь меня остановить. НЕТ!')
        print()

        counter = 0

        while counter < 6:
            srtike_list = ['атака', 'парирование']
            strike = choice(srtike_list)

            hit = input('Мегатрон собирается нанести удар. Ты будешь парировать или атаковать (атака/парирование)')
            if hit == strike:
                print('Отлично! Верное решение')
                autobot1.powerful += 25
            else:
                print('О нет! Мегатрон смог нанести удар.')
                autobot1.powerful -= 200
            counter += 1

        if autobot1.powerful > 0:
            print()
            print('Отлично! Мы его отключили. Один выстрел и всё готово.')
            print('**БAM**')
            print('Поздравляю! Спустя столько лет тирании десептиконов мы победили! Мегатрон уничтожен.')
            print()
            print('Игра пройденна! Тебе удалось остановить войну между трансформерами')
        else:
            print()
            print('Нет! Ты допустил слишком много ошибок')
            print('После череды сокрушительных ударов Мегатрон победил. Сначала тебя, а после всех автоботов')
            print('**GAME OVER**')

    if player_choice == '2':

        print('Отлично', autobot2.name, 'был доблесным воином!')
        print()
        print('Автоботы, К БОЮ!')
        print()

        game_ok = True  # Эта переменная служит для понимания не закончился ли игравой цикл
        decepticon_num = 1  # Эта переменная служит для понимания какой по счёту сейчас враг
        deception = None  # Эта переменная служит для упрощения кода ей присваиватся определённый десептикон

        # Начало игрового цикла
        while game_ok:
            print('Твой враг уже приближается!')
            print('*сейчас тебе покажут случайную характеристику врага, по ней тебе нужно решить. Сражаться или '
                  'отступить!')
            print()
            if decepticon_num == 1:
                # Вывод случайной характеристики
                data_ch = choice(characteristic)
                if data_ch == 'power':
                    print('Сила десептикона:', deception1.power)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot2.powerful < deception1.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot2.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на +90')
                            autobot2.powerful += 90
                if data_ch == 'health':
                    print('Уровень здоровья десептикона:', deception1.health)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot2.powerful < deception1.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot2.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot2.powerful += 90
                if data_ch == 'armor':
                    print('Уровень брони десептикона:', deception1.armor)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot2.powerful < deception1.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot2.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot2.powerful += 90
                if data_ch == 'speed':
                    print('Скорость десептикона:', deception1.speed)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot2.powerful < deception1.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot2.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot2.powerful += 90
                decepticon_num += 1

            if decepticon_num == 2:
                # Вывод случайной характеристики
                data_ch = choice(characteristic)
                if data_ch == 'power':
                    print('Сила десептикона:', deception2.power)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot2.powerful < deception2.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot2.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot2.powerful += 90
                if data_ch == 'health':
                    print('Уровень здоровья десептикона:', deception2.health)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot2.powerful < deception2.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot2.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot2.powerful += 90
                if data_ch == 'armor':
                    print('Уровень брони десептикона:', deception2.armor)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot2.powerful < deception2.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot2.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot2.powerful += 90
                if data_ch == 'speed':
                    print('Скорость десептикона:', deception2.speed)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot2.powerful < deception2.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot2.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot2.powerful += 90
                decepticon_num += 1

            if decepticon_num == 3:
                data_ch = choice(characteristic)
                if data_ch == 'power':
                    print('Сила десептикона:', deception3.power)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot2.powerful < deception3.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot2.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot2.powerful += 90
                if data_ch == 'health':
                    print('Уровень здоровья десептикона:', deception3.health)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot2.powerful < deception3.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot2.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot2.powerful += 90
                if data_ch == 'armor':
                    print('Уровень брони десептикона:', deception3.armor)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot2.powerful < deception3.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot2.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot2.powerful += 90
                if data_ch == 'speed':
                    print('Скорость десептикона:', deception3.speed)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot2.powerful < deception3.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot2.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot2.powerful += 90
                decepticon_num += 1

            if decepticon_num == 4:
                data_ch = choice(characteristic)
                if data_ch == 'power':
                    print('Сила десептикона:', deception4.power)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot2.powerful < deception4.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot2.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                if data_ch == 'health':
                    print('Уровень здоровья десептикона:', deception4.health)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot2.powerful < deception4.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot2.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot2.powerful += 90
                if data_ch == 'armor':
                    print('Уровень брони десептикона:', deception4.armor)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot2.powerful < deception4.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot2.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot2.powerful += 90
                if data_ch == 'speed':
                    print('Скорость десептикона:', deception4.speed)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot2.powerful < deception4.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot2.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot2.powerful += 90
                decepticon_num += 1

            if decepticon_num == 5:
                data_ch = choice(characteristic)
                if data_ch == 'power':
                    print('Сила десептикона:', deception5.power)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot2.powerful < deception5.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot2.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot2.powerful += 90
                if data_ch == 'health':
                    print('Уровень здоровья десептикона:', deception5.health)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot2.powerful < deception5.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot2.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot2.powerful += 90
                if data_ch == 'armor':
                    print('Уровень брони десептикона:', deception5.armor)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot2.powerful < deception5.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot2.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot2.powerful += 90
                if data_ch == 'speed':
                    print('Скорость десептикона:', deception5.speed)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot2.powerful < deception5.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot2.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot2.powerful += 90
                game_ok = False
        # все условные операторы выше ОДИНАКОВЫЕ

        #
        print()
        print('Не может быть! Нам удалось прорваться сквозь полчища десептиконов. Мегатрон уже близко.')
        print('Тебе нужно лишь тянуть время, пока мы отключаем его от этого оружия. Запомни!')
        print('Он слишком силён и не предсказуем. Бей и парируй! Удачи!')
        print()
        print('МЕГАТРОН: Что. Кто это? Ха. Жалкий автобот. Ты правда думаешь, что сможешь меня остановить. НЕТ!')
        print()

        counter = 0

        while counter < 6:
            srtike_list = ['атака', 'парирование']
            strike = choice(srtike_list)

            hit = input('Мегатрон собирается нанести удар. Ты будешь парировать или атаковать (атака/парирование)')
            if hit == strike:
                print('Отлично! Верное решение')
                autobot2.powerful += 25
            else:
                print('О нет! Мегатрон смог нанести удар.')
                autobot2.powerful -= 200
            counter += 1

        if counter >= 6:
            print()
            print('Отлично! Мы его отключили. Один выстрел и всё готово.')
            print('**БAM**')
            print('Поздравляю! Спустя столько лет тирании десептиконов мы победили! Мегатрон уничтожен.')
            print()
            print('Игра пройденна! Тебе удалось остановить войну между трансформерами')
        else:
            print()
            print('Нет! Ты допустил слишком много ошибок')
            print('После череды сокрушительных ударов Мегатрон победил. Сначала тебя, а после всех автоботов')
            print('**GAME OVER**')

    if player_choice == '3':
        print('Отлично', autobot3.name, 'был доблесным воином!')
        print()
        print('Автоботы, К БОЮ!')
        print()

        game_ok = True  # Эта переменная служит для понимания не закончился ли игравой цикл
        decepticon_num = 1  # Эта переменная служит для понимания какой по счёту сейчас враг
        deception = None  # Эта переменная служит для упрощения кода ей присваиватся определённый десептикон

        # Начало игрового цикла
        while game_ok:
            print('Твой враг уже приближается!')
            print('*сейчас тебе покажут случайную характеристику врага, по ней тебе нужно решить. Сражаться или '
                  'отступить!')
            print()
            if decepticon_num == 1:
                # Вывод случайной характеристики
                data_ch = choice(characteristic)
                if data_ch == 'power':
                    print('Сила десептикона:', deception1.power)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot3.powerful < deception1.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot3.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot3.powerful += 90
                if data_ch == 'health':
                    print('Уровень здоровья десептикона:', deception1.health)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot3.powerful < deception1.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot3.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot3.powerful += 90
                if data_ch == 'armor':
                    print('Уровень брони десептикона:', deception1.armor)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot3.powerful < deception1.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot3.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot3.powerful += 90
                if data_ch == 'speed':
                    print('Скорость десептикона:', deception1.speed)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot3.powerful < deception1.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot3.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot3.powerful += 90
                decepticon_num += 1

            if decepticon_num == 2:
                # Вывод случайной характеристики
                data_ch = choice(characteristic)
                if data_ch == 'power':
                    print('Сила десептикона:', deception2.power)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot3.powerful < deception2.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot3.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot3.powerful += 90
                if data_ch == 'health':
                    print('Уровень здоровья десептикона:', deception2.health)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot3.powerful < deception2.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot3.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot3.powerful += 90
                if data_ch == 'armor':
                    print('Уровень брони десептикона:', deception2.armor)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot3.powerful < deception2.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot3.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot3.powerful += 90
                if data_ch == 'speed':
                    print('Скорость десептикона:', deception2.speed)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot3.powerful < deception2.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot3.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot3.powerful += 90
                decepticon_num += 1

            if decepticon_num == 3:
                data_ch = choice(characteristic)
                if data_ch == 'power':
                    print('Сила десептикона:', deception3.power)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot3.powerful < deception3.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot3.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot3.powerful += 90
                if data_ch == 'health':
                    print('Уровень здоровья десептикона:', deception3.health)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot3.powerful < deception3.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot1.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot3.powerful += 90
                if data_ch == 'armor':
                    print('Уровень брони десептикона:', deception3.armor)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot3.powerful < deception3.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot3.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot3.powerful += 90
                if data_ch == 'speed':
                    print('Скорость десептикона:', deception3.speed)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot3.powerful < deception3.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot3.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot3.powerful += 90
                decepticon_num += 1

            if decepticon_num == 4:
                data_ch = choice(characteristic)
                if data_ch == 'power':
                    print('Сила десептикона:', deception4.power)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot3.powerful < deception4.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot3.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot3.powerful += 90
                if data_ch == 'health':
                    print('Уровень здоровья десептикона:', deception4.health)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot3.powerful < deception4.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot3.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot3.powerful += 90
                if data_ch == 'armor':
                    print('Уровень брони десептикона:', deception4.armor)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot3.powerful < deception4.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot3.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot3.powerful += 90
                if data_ch == 'speed':
                    print('Скорость десептикона:', deception4.speed)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot3.powerful < deception4.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot3.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot3.powerful += 90
                decepticon_num += 1

            if decepticon_num == 5:
                data_ch = choice(characteristic)
                if data_ch == 'power':
                    print('Сила десептикона:', deception5.power)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot3.powerful < deception5.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot3.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot3.powerful += 90
                if data_ch == 'health':
                    print('Уровень здоровья десептикона:', deception5.health)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot3.powerful < deception5.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot3.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot3.powerful += 90
                if data_ch == 'armor':
                    print('Уровень брони десептикона:', deception5.armor)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot3.powerful < deception5.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot3.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot3.powerful += 90
                if data_ch == 'speed':
                    print('Скорость десептикона:', deception5.speed)
                    question = input('Ты будешь биться (да/нет)')
                    if question == 'да':
                        if autobot3.powerful < deception5.powerful:
                            print(
                                'Этот десептикон оказался слишком силён. После сокрушительных ударов тебе удалось '
                                'выжить, '
                                'но ты ослабеваешь на -90')
                            autobot3.powerful -= 90
                        else:
                            print(
                                'Тебе удалось одержать победу из запчастей ты улучшил снаряжение и становишься силнее '
                                'на '
                                '+90')
                            autobot3.powerful += 90
                game_ok = False
        # все условные операторы выше ОДИНАКОВЫЕ

        #
        print()
        print('Не может быть! Нам удалось прорваться сквозь полчища десептиконов. Мегатрон уже близко.')
        print('Тебе нужно лишь тянуть время, пока мы отключаем его от этого оружия. Запомни!')
        print('Он слишком силён и не предсказуем. Бей и парируй! Удачи!')
        print()
        print('МЕГАТРОН: Что. Кто это? Ха. Жалкий автобот. Ты правда думаешь, что сможешь меня остановить. НЕТ!')
        print()

        counter = 0

        while counter < 6:
            srtike_list = ['атака', 'парирование']
            strike = choice(srtike_list)

            hit = input('Мегатрон собирается нанести удар. Ты будешь парировать или атаковать (атака/парирование)')
            if hit == strike:
                print('Отлично! Верное решение')
                autobot3.powerful += 25
            else:
                print('О нет! Мегатрон смог нанести удар.')
                autobot3.powerful -= 200
            counter += 1

        if counter >= 6:
            print()
            print('Отлично! Мы его отключили. Один выстрел и всё готово.')
            print('**БAM**')
            print('Поздравляю! Спустя столько лет тирании десептиконов мы победили! Мегатрон уничтожен.')
            print()
            print('Игра пройденна! Тебе удалось остановить войну между трансформерами')
        else:
            print()
            print('Нет! Ты допустил слишком много ошибок')
            print('После череды сокрушительных ударов Мегатрон победил. Сначала тебя, а после всех автоботов')
            print('**GAME OVER**')

print("Вот и сказочке конец!")
