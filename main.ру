import asyncio
from aiogram import Bot, Dispatcher, types
from aiogram.filters import Command
import os

BOT_TOKEN = os.getenv("BOT_TOKEN")

bot = Bot(token=BOT_TOKEN)
dp = Dispatcher()

@dp.message(Command("start"))
async def start(message: types.Message):
    keyboard = types.ReplyKeyboardMarkup(resize_keyboard=True)
    keyboard.add("📱 iPhone", "🎧 AirPods")
    keyboard.add("💻 MacBook", "📟 iPad")
    await message.answer(
        "Добро пожаловать в Turan Electronics!\n\n"
        "Выберите категорию:",
        reply_markup=keyboard
    )

@dp.message(lambda m: m.text in ["📱 iPhone", "🎧 AirPods", "💻 MacBook", "📟 iPad"])
async def show_products(message: types.Message):
    category = message.text
    products = {
        "📱 iPhone": ["iPhone 17 Pro 256GB", "iPhone 17 Pro Max 512GB"],
        "🎧 AirPods": ["AirPods 4", "AirPods Pro 2"],
        "💻 MacBook": ["MacBook Air M3", "MacBook Pro M4"],
        "📟 iPad": ["iPad Pro M4 11\"", "iPad Air 2024"],
    }
    msg = f"{category}\n\n" + "\n".join(f"• {p}" for p in products[category])
    await message.answer(msg)

async def main():
    print("Бот запущен!")
    await dp.start_polling(bot)

if __name__ == "__main__":
    asyncio.run(main())
