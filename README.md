# Shopping---Cart---OOP
## Features - Classes + OOP architecture - Add/Remove shopping items - Professional receipt generation - E-commerce production logic
class Product:
    def __init__(self, name, price):
        self.name = name
        self.price = price
        
    def display(self):
        return f"📱 {self.name} - ${self.price:,}"
        

class ShoppingCart:
    def __init__(self):
        self.items = []
        
    def add_item(self, product, Qty=1):
        self.items.append({"product": product, "Qty": Qty})
        return f"✅ {Qty} x {product.name}"
        
    def show_receipt(self):
        if not self.items:
            return "🛒 Cart empty!"
        
        total = 0
        print("🛒 Your Receipt:")
        for item in self.items:
            subtotal = item["product"].price * item["Qty"]
            total += subtotal
            print(f"{item['Qty']}x {item['product'].display()} = ${subtotal:,}")
        print(f"💰 Total: ${total:,}")
        return total
    
    def remove_item(self, position):
        if 0 <= position < len(self.items):
            removed = self.items.pop(position)
            return f"🗑️ Removed {removed['product'].name}"
        else:
            return "🛒 Invalid position"
            

# Example usage
phone = Product("iPhone 14", 480000)
laptop = Product("MacBook Air", 840000)
headphones = Product("AirPods", 4800)

my_cart = ShoppingCart()

print(phone.display())
print(laptop.display())
print(my_cart.add_item(phone, 4))
print(my_cart.add_item(headphones))
print(my_cart.add_item(laptop))
my_cart.show_receipt()
print(my_cart.remove_item(1))
my_cart.show_receipt()
