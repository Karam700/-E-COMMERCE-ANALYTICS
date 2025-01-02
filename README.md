import pandas as pd
import matplotlib.pyplot as plt


file_path = r"C:\Users\كرم\Downloads\sample_ecommerce_dataset.csv"
try:
    df = pd.read_csv(file_path)
except FileNotFoundError:
    print(f"Error: File '{file_path}' not found. Please check the file path.")
    exit()


print("\nData Summary:")
print(df.describe())


if "Price" in df.columns and "Total Revenue" in df.columns:
    average_price = df["Price"].mean()
    total_revenue = df["Total Revenue"].sum()
    print("\nCalculations:")
    print(f"Average Price: {average_price:.2f}")
    print(f"Total Revenue: {total_revenue:.2f}")
else:
    print("Error: Required columns 'Price' and 'Total Revenue' not found in the dataset.")
    exit()


if "Product Name" in df.columns and "Price" in df.columns:
    plt.figure(figsize=(10, 6))
    plt.bar(df["Product Name"], df["Price"], color="blue")
    plt.title("Product Prices")
    plt.xlabel("Product Name")
    plt.ylabel("Price")
    plt.xticks(rotation=90)
    plt.tight_layout()
    plt.show()
else:
    print("Error: Required columns 'Product Name' and 'Price' not found in the dataset.")


if "Product Name" in df.columns and "Total Revenue" in df.columns:
    plt.figure(figsize=(10, 6))
    plt.bar(df["Product Name"], df["Total Revenue"], color="green")
    plt.title("Total Revenue per Product")
    plt.xlabel("Product Name")
    plt.ylabel("Total Revenue")
    plt.xticks(rotation=90)
    plt.tight_layout()
    plt.show()
else:
    print("Error: Required columns 'Product Name' and 'Total Revenue' not found in the dataset.")


