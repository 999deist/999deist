from telegram.ext.callbackcontext import CallbackContext

from telegram.ext.commandhandler import CommandHandler

from telegram.ext.filters import Filters

from telegram.ext.messagehandler import MessageHandler

from telegram.ext.updater import Updater

from telegram.update import Update

BOT_KEY = "<YOUR_BOT_KEY_HERE>"

def start(update: Update, context: CallbackContext):

welcome_message = "Welcome to this bot!"

update.message.reply_text(welcome_message, parse_mode="html")

def unknown_text(update: Update, context: CallbackContext):

update.message.reply_text(f"If you need support please contact example@email.com.")

def _add_handlers(updater):

updater.dispatcher.add_handler(CommandHandler("start", start))

updater.dispatcher.add_handler(MessageHandler(Filters.text, unknown_text))

if __name__ == "__main__":

updater = Updater(BOT_KEY, use_context=True)

_add_handlers(updater)

print("starting to poll...")

updater.start_polling()

