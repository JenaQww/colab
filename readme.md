numbers = []
while True:
    user_input = input("Введи число (или 'стоп', чтобы закончить): ")
    if user_input.lower() == "стоп":
        break
    try:
        num = float(user_input)
        numbers.append(num)
    except ValueError:
        print("Это не число, попробуй ещё раз.")

if numbers:
    total = sum(numbers)
    avg = total / len(numbers)
    minimum = min(numbers)
    maximum = max(numbers)

    print("\nРезультаты:")
    print(f"Сумма: {total}")
    print(f"Среднее: {avg}")
    print(f"Минимум: {minimum}")
    print(f"Максимум: {maximum}")
else:
    print("Ты не ввёл ни одного числа.")
