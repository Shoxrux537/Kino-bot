# Kino-bot
from telegram import Update
from telegram.ext import ApplicationBuilder, CommandHandler, ContextTypes

BOT_TOKEN = "8174484348:AAHL10w7sEoU6RXAdFZTDs8Y0I9mhLCR0ek"

async def start(update: Update, context: ContextTypes.DEFAULT_TYPE):
    await update.message.reply_text("Salom! Qaysi kinoni ko‘rmoqchisiz?\nMasalan: /kino domchilik")

async def kino(update: Update, context: ContextTypes.DEFAULT_TYPE):
    query = ' '.join(context.args).lower()
    if query == 'domchilik':
        await update.message.reply_text("Mana sizga 'Domchilik' filmi:")
        await update.message.reply_video("1002695285941")
    else:
        await update.message.reply_text("Kechirasiz, bu film hozircha mavjud emas.")

app = ApplicationBuilder().token(BOT_TOKEN).build()

app.add_handler(CommandHandler("start", start))
app.add_handler(CommandHandler("kino", kino))

app.run_polling()
