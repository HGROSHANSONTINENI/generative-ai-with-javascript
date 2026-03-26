
class Inventory {
    constructor() {
        this.items = [];
    }

    addItem(item) {
        this.items.push(item);
        return `${item} added to inventory.`;
    }

    listItems() {
        if (this.items.length === 0) return "Inventory is empty.";
        return "Inventory:\n" + this.items.map((i, idx) => `${idx + 1}. ${i}`).join("\n");
    }


    searchItem(item) {
        return this.items.includes(item)
            ? `${item} is in the inventory.`
            : `${item} is not found in the inventory.`;
    }
}


class Abacus {
    add(a, b) {
        return a + b;
    }

    subtract(a, b) {
        return a - b;
    }

    multiply(a, b) {
        return a * b;
    }

    divide(a, b) {
        if (b === 0) return "Error: Division by zero!";
        return a / b;
    }
}


const scipioInventory = new Inventory();
const scipioAbacus = new Abacus();

scipioInventory.addItem("Scroll of Tactics");
scipioInventory.addItem("Scroll of Food Supply");
scipioInventory.addItem("Taxation Scroll");


console.log(scipioInventory.listItems());
console.log(scipioInventory.searchItem("Scroll of Tactics"));
console.log(scipioInventory.searchItem("Scroll of Magic"));

console.log("Abacus Operations:");
console.log("5 + 7 =", scipioAbacus.add(5, 7));
console.log("10 - 4 =", scipioAbacus.subtract(10, 4));
console.log("6 * 3 =", scipioAbacus.multiply(6, 3));
console.log("12 / 4 =", scipioAbacus.divide(12, 4));
console.log("12 / 0 =", scipioAbacus.divide(12, 0));