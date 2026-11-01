import csv

# Пример входных данных: каждая строка — это «товар;количество;цена»
raw_data = [
    "яблоко;3;50",
    "банан;2;40",
    "молоко;1;80",
    "хлеб;2;60",
]

rows = []
for line in raw_data:
    parts = line.strip().split(";")
    if len(parts) != 3:
        continue  # пропускаем строки с неправильным форматом
    product, quantity_str, price_str = parts
    try:
        quantity = int(quantity_str)
        price = float(price_str)
    except ValueError:
        continue
    total_price = quantity * price
    rows.append({
        "product": product,
        "quantity": quantity,
        "price": price,
        "total": total_price,
    })

output_file = "funnel.csv"
with open(output_file, mode="w", newline="", encoding="utf-8") as f:
    fieldnames = ["product", "quantity", "price", "total"]
    writer = csv.DictWriter(f, fieldnames=fieldnames)
    writer.writeheader()
    writer.writerows(rows)

print(f"Данные успешно записаны в {output_file}")
