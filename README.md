# bot-calculator

import telebot

TOKEN = "8294674212:AAGLcr0I9gdWV1IVQa7sPNqbTDyj0YGjlL8"

bot = telebot.TeleBot(TOKEN)

@bot.message_handler(commands=['start'])
def start(message):
    bot.send_message(
        message.chat.id,
        "Привіт! \n"
        "Надішли мені математичний вираз.\n"
        "Наприклад: 2+3*4"
    )

@bot.message_handler(func=lambda message: True)
def calculate(message):
    try:
        result = eval(message.text)
        bot.send_message(message.chat.id, f"Результат: {result}")
    except:
        bot.send_message(message.chat.id, " Помилка у виразі")

bot.polling()
