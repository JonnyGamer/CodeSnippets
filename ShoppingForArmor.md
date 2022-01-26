You asked:
```
1: Is there any way to shorten this code, so it wouldn't be annoying to add new items to the list? 
```

There is a way!

Here is your new shop function!

We can discuss this together.

```swift
func shop() {
    while true {
        
        // Asks whether you want to buy armor or weapons
        print("What type of gear are you looking for?")
        print("""
        1. Armor
        2. Weapons
        """)
        var armorweapons = ericReadLine()
        
        // To add new armor, just add to this list!
        var armor: [(name: String, price: Int, health: Int)] = [
            ("Chainmail Armor", 200, 80),
            ("Iron Armor", 700, 100),
            ("Adamantine Armor", 2000, 400),
            ("Iron Man Armor", 5000, 400),
            ("Divine Fortune", 20000, 1200),
            ("Plot Armor", 100000, 800)
        ]
        
        // Lists the armor items
        func listArmor() {
            print("What would you like to buy?")
            for i in 0..<armor.count {
                print("\(i+1). \(armor[i].0) | \(armor[i].1) coins || \(armor[i].2) health")
            }
            print("Type Enter to go back")
        }
        
        // Determines whether you can actually make an armor purchase
        func attemptToPurchaseArmor(item: Int) {
            if item == 0 || item > armor.count {
                print("Our list isn't that big.")
                return
            }
            
            let itemYouWant = armor[item - 1]
            if itemYouWant.price > coins - 1 {
                print("You're too broke to make this purchase. Welcome to the real world, pessant.")
            } else {
                print("You bought a set of \(itemYouWant.name) for \(itemYouWant.price) coins.")
                items.append(itemYouWant.name)
                health = itemYouWant.health
                coins -= itemYouWant.price
            }
        }
        
        // You have selected to view the armor category
        if armorweapons == "1" {
            listArmor()
            
            let armorWanted = ericReadLine()
            attemptToPurchaseArmor(item: Int(armorWanted) ?? 0)
        }
        
    }
}
```
