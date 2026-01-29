import telebot
import os

TOKEN = os.environ.get("8580915676:AAFe1ixEcrMoFTQXcUUx3kFPcwNdlo26sWA")  # Render এ environment variable ব্যবহার হবে
bot = telebot.TeleBot(TOKEN)

# /start command
@bot.message_handler(commands=['start'])
def start(message):
    bot.reply_to(message, f"🔥 আরে {message.from_user.first_name}! আমি InfoBot 😎\nব্যবহার করতে /info টাইপ করো।")

# /info command
@bot.message_handler(commands=['info'])
def info(message):
    user = message.from_user
    chat = message.chat

    info_text = f"""
👤 ইউজার ইনফো:
নাম: {user.first_name} {user.last_name if user.last_name else ''}
ইউজারনেম: @{user.username if user.username else 'নাই'}
ইউজার আইডি: {user.id}
চ্যাট টাইপ: {chat.type}
চ্যাট আইডি: {chat.id}
"""
    bot.reply_to(message, info_text)

bot.infinity_polling()
