from telegram.ext import*
import response as r


API_KEY="1929363750:AAFj7nvJMrx26EKrhrw2HWmygIdnBKPlWOE"

def help(update,context):
    update.message.reply_text("yes iam hear to help")
def start(update,context):
    update.message.reply_text("ask something")
def handle_message(update,context):
    text = str(update.message.text).lower()
    response = r.sample(text)
    update.message.reply_text(response)

def error(update,context):
    print("error")

def main():
 updater= Updater(API_KEY,use_context = True)
 dp =updater.dispatcher
 dp.add_handler(CommandHandler("start",start))
 dp.add_handler(CommandHandler("help",help))
 dp.add_error_handler(error)
 dp.add_handler(MessageHandler(Filters.text,handle_message))

 updater.start_polling()
 updater.idle()

main()




