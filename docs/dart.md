# Dart Exercises(Lab 2)
## Exercise 1: Named Parameters
DartPad link: https://dartpad.dev/?s=1
**Output:** 
- Total: 300.0
- Total: 270.0
- Total: 75.0

**Explanation:** `required` forces the caller to give `unit` and `quantity`. `discount` has a default of 0, so it is optional. Named parameters can be passed in any order  because they are matched by name.

## Exercise 2: Null safety
DartPad Code: 
/*String? findTown(String code){
    const towns={'DLA': 'Douala', 'YDE': 'Yaounde'};
    return town[code];
}
void main(){
    print(findTown('DLA') ?? 'Unknown town');
    print(findTown('XXX') ?? 'Unknown town');
}*/
**Output:**
- Douala
- Unknown town

**Explanation:** The return type `String?` means the funtion can return a text or `null`. The `?` marks the type as nullable. Looking up a key that does not exist in a map(here `'XXX'`) returns `null`, so `findTown` returns `null` for an unknown code, as the exercise requires. The `??` operator is the "if null" operator: `findTown('XXX') ?? 'Unkown town'` uses the result when it exists, and otherwise uses `'Unknown town'`. This is **null safety**:Dart seperates types that can be null from those that cannot, and forces me to handle the "no value" case. Without `??`, the program would print `null`, and using the value where a normal `String` is expected would cause a co,pile error.

## Exercise 3: where, map and fold
/*void main(){
    final prices = [250, 600, 900, 120, 750];
    print(prices.where((p)=>p>500).toList());
    print(prices.map((p)=> p*1.1).toList());
    print(prices.fold(0, (sum,p)=>sum + p));
}*/
**Output:**
- [600, 900, 750]
- [275, 660, 990.0000000000001, 132, 825.0000000000001]
- 2620
**Explanation:**`where` **filters** a list: it keeps only the items for which the condition is true, so `p>500` keeps 600, 900 and 750. map*transforms* every item into a new one: p * 1.1 increases each price by 10%. fold *reduces* the whole list to a single value: it starts at 0 and adds each price to the running sum, giving the total 262. where and map return lazy iterables, so i call .tolist() to see them as list.None af these methods change the orignal list.

## Exercise 4: Class, const constructor, getter, describe() and async
/*class Product{
    final String name;
    final double price;
    const Product(this.name, this.price);
    String get label=>'$name (${price.toStringAsFixed(0)} FCFA)';
    void describe() => print('Product: $label');
}
Future<String> waitOneSecond() async{
    await Future.delayed(const Duration(seconds: 1));
    return 'Done waiting';
}
void main() async{
    const Product('Rice', 800).describe();
    print(await waitOneSecond());
}*/
**Output:**
Product: Rice(800 FCFA)
Done waiting

**Explanation:** The `Product` class has two `final` fields, which are assigned once and cannot change. The `const` construct lets Dart create the object at compile time, so same instance can be refused. `label` is a **getter**:it looks like a field but is computed each time from `name` and `price`. `describe()` is a method that prints the product using that getter.
`waitOneSecond` is an **async** function: it returns s `Future<String>`, which is a value that will be availabvle later. Inside it, `await Future.delayed(...)` pauses that for one second without freezing the app, then it returns the text. In `main`, `await` waits for the result before printing it. Because `main` uses `await`, it is also marked `async`.