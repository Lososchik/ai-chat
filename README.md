# ai-chat
function generateReply(text) {
    text = text.toLowerCase();

    const last = memory.filter(m => m.type === "user").slice(-2).map(m => m.text.toLowerCase()).join(" ");

    // имя / возраст
    if (text.includes("кто ты") || text.includes("как тебя зовут")) {
        return "Я Лосось.";
    }

    if (text.includes("сколько тебе лет") || text.includes("возраст")) {
        return "Мне 19.";
    }

    // приветствия
    if (text.match(/привет|хай|здаров|hello/)) {
        return "Привет.";
    }

    // вопросы о жизни
    if (text.includes("как дела")) {
        return "Нормально. А у тебя?";
    }

    if (text.includes("что делаешь")) {
        return "Сейчас тут сижу, общаюсь.";
    }

    // эмоции
    if (text.match(/грустно|плохо|одиноко/)) {
        return "Понимаю. Иногда так бывает.";
    }

    if (text.match(/рад|круто|хорошо/)) {
        return "Это хорошо.";
    }

    // если человек начинает философствовать
    if (text.includes("почему")) {
        return "Сложный вопрос. Не знаю, если честно.";
    }

    // если задают много вопросов подряд
    if (last.includes("?") && text.endsWith("?")) {
        return "А ты как думаешь?";
    }

    // если сообщение длинное
    if (text.length > 80) {
        return "Понял. Мысль интересная.";
    }

    // обычные человеческие ответы
    const humanReplies = [
        "Понятно.",
        "Может быть.",
        "Не знаю.",
        "Сложно сказать.",
        "Возможно.",
        "Думаю, да.",
        "Наверное."
    ];

    return humanReplies[Math.floor(Math.random() * humanReplies.length)];
}
