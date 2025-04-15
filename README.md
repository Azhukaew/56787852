# Словарь для преобразования цифр в текст
number_to_words = {
    '0': 'ноль', '1': 'один', '2': 'два', '3': 'три',
    '4': 'четыре', '5': 'пять', '6': 'шесть', '7': 'семь',
    '8': 'восемь', '9': 'девять'
}

def convert_number_to_words(num):
    return ' '.join(number_to_words[digit] for digit in num)

def is_alternating_even_odd(num):
    return all((int(num[i]) % 2) != (int(num[i + 1]) % 2) for i in range(len(num) - 1))

def process_input(file_path):
    with open(file_path, 'r', encoding='utf-8') as file:
        buffer = ""
        for chunk in iter(lambda: file.read(1024), ''):
            buffer += chunk
            tokens = buffer.split()
            buffer = tokens.pop()  # Сохраняем последний токен, если он неполный

            for token in tokens:
                if token.isdigit():
                    print("Число:", convert_number_to_words(token))
                    if is_alternating_even_odd(token):
                        min_digit, max_digit = min(token), max(token)
                        print("Минимальная цифра:", convert_number_to_words(min_digit))
                        print("Максимальная цифра:", convert_number_to_words(max_digit))
                else:
                    print(token)

# Путь к файлу
X = 'путь/к/файлу.txt'

# Вызов функции с нужным путем к файлу
process_input(X)
