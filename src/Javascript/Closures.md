# Closures 
- Are formed when an inner function has access to the variables of its outer function, even after the outer function has finished executing. 
- Allows for the encapsulation of variables within a function's scope, meaning that variables defined within a function are not accessible from outside the function unless explicitly exposed. 
- Allows data privacy by allowing functions to have private varaibles. These variables are accessible only within the function's scope and cannot be modified directly from the outside. 
- Can maintain the state of varaiables across multiple function calls since inner functions retain access to the outer functions variables, it can access and modify them as needed. 
- Commonly used in callback functions and aysnc operations. When a callback function is pased to another function, it retains access to the variables in its outer scope, allowing it to use those variables when the callback is eventually invoked. 

```JS 
function createInventory() {
    let ingredients = {}; // This is a private variable within the closure scope

    return {
        addIngredient: function(name, quantity) {
            if (ingredients[name]) {
                ingredients[name] += quantity;
            } else {
                ingredients[name] = quantity;
            }
            console.log(`Added ${quantity} units of ${name} to the inventory.`);
        },
        useIngredient: function(name, quantity) {
            if (ingredients[name]) {
                if (ingredients[name] >= quantity) {
                    ingredients[name] -= quantity;
                    console.log(`Used ${quantity} units of ${name} from the inventory.`);
                } else {
                    console.log(`Not enough ${name} in the inventory.`);
                }
            } else {
                console.log(`Ingredient ${name} not found in the inventory.`);
            }
        },
        getInventory: function() {
            return ingredients;
        }
    };
}

// Create an instance of inventory
const inventory = createInventory();

// Add ingredients to the inventory
inventory.addIngredient('Tomato', 10);
inventory.addIngredient('Onion', 5);
inventory.addIngredient('Cheese', 20);

// Use ingredients from the inventory
inventory.useIngredient('Tomato', 3);
inventory.useIngredient('Onion', 2);
inventory.useIngredient('Cheese', 25); // This should log "Not enough Cheese in the inventory."

// Get the current inventory
console.log(inventory.getInventory());
```
> In this example, createInventory is a function that creates a closure over the ingredients object. It returns an object with three methods: addIngredient, useIngredient, and getInventory. These methods have access to the ingredients variable even after createInventory has finished executing, forming a closure. This allows us to maintain and manipulate the inventory state over time.

```JS 
function createChef(chefName) {
    let name = chefName; // Private variable accessible within the closure

    return function(food) {
        console.log(`${name} is cooking ${food}!`);
    };
}

// Create chef instances
const chef1 = createChef('Chef John');
const chef2 = createChef('Chef Emily');

// Call the chef functions
chef1('spaghetti');
chef2('salad');
```
>In this example, the createChef function returns a function that logs the chef's name and the food they're cooking. The returned function has access to the chefName variable even after createChef has finished executing, forming a closure. Each time we call createChef, we create a new instance of a chef with their own name, and each chef instance retains access to their own name through the closure.

#  Benefits of Closures
- ✅ encapsulation of data within their scope, preventing external access and modification. This helps maintain data integrity and reduces unintended side effects.
- ✅ maintaining state by allow functions to retain access to variables defined in their lexical environment, even after the outer function has finished executing.
- ✅ data privacy since variables enclosed within a closure are not accessible from outside the closure, providing a level of security