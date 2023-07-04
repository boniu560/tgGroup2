pip install python-telegram-bot
from telegram import InlineKeyboardButton, InlineKeyboardMarkup, Update
from telegram.ext import CallbackContext, CommandHandler, CallbackQueryHandler, Filters, MessageHandler, Updater

# Handler for the '/start' command
def start(update: Update, context: CallbackContext):
    chat_id = update.message.chat_id
    message = "Hi, I am your bot. Click the button below for payment."
    
    # Create an inline keyboard with the payment button
    button = InlineKeyboardButton("Payment 50 USD", callback_data="payment")
    keyboard = InlineKeyboardMarkup([[button]])
    
    # Send the welcome message with the keyboard
    context.bot.send_message(chat_id=chat_id, text=message, reply_markup=keyboard)

# Handler for the payment button
def payment_button(update: Update, context: CallbackContext):
    query = update.callback_query
    chat_id = query.message.chat_id
    
    # Get the user's Metamask account number
    metamask_account = "Your Metamask account number"
    
    # Send the Metamask account number as a message
    context.bot.send_message(chat_id=chat_id, text=metamask_account)

# Handler for text messages
def echo(update: Update, context: CallbackContext):
    chat_id = update.message.chat_id
    text = update.message.text
    if text == "/start":
        start(update, context)

# Set up the bot and handlers
def main():
    # Create the Updater and pass your bot token
    updater = Updater("6397976173:AAHGX2LU4syfNfGK33izj0ei9U2_DtRVF2c", use_context=True)

    # Get the dispatcher to register handlers
    dp = updater.dispatcher

    # Add handlers
    dp.add_handler(CommandHandler("start", start))
    dp.add_handler(CallbackQueryHandler(payment_button))
    dp.add_handler(MessageHandler(Filters.text, echo))

    # Start the bot
    updater.start_polling()

    # Run the bot until you press Ctrl-C
    updater.idle()

if __name__ == '__main__':
    main()
