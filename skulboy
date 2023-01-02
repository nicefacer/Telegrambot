import openai
import telegram

# Replace YOUR_API_KEY and YOUR_TELEGRAM_TOKEN with your actual API key and Telegram token
openai.api_key = "YOUR_API_KEY"
telegram_bot = telegram.Bot("YOUR_TELEGRAM_TOKEN")

def generate_response(prompt):
  completions = openai.Completion.create(
    engine="text-davinci-002",
    prompt=prompt,
    max_tokens=1024,
    temperature=0.5,
  )

  message = completions.choices[0].text
  return message

def handle_message(message):
  prompt = message.text
  response = generate_response(prompt)
  telegram_bot.send_message(chat_id=message.chat_id, text=response)

updater = telegram.ext.Updater("YOUR_TELEGRAM_TOKEN")
dispatcher = updater.dispatcher

# Add a handler for the "message" event
dispatcher.add_handler(telegram.ext.MessageHandler(telegram.ext.Filters.text, handle_message))

# Start the bot
updater.start_polling()
