# LAB 3 SOLUTIONS
## QUESTION1 
```question1.js
const shoppingCart = (function (){
    let basket =[];
    return{
        upsertItem:function(item){
            for (const elem of basket) {
                if(elem.id === item.id){
elem.product = item.product;
elem.count = item.count;
return item;
                }   
            }
basket.push(item);

        },
        getItemsCount: function(){
return basket.length;
        },
        getTotalPrice: function(){
return basket.reduce((total, item) => total + (item.product.price * item.count), 0);
        },
        removeItemById: function(id){
            return basket.splice(id,1);
        }
    } 
})();

const item1 = { id: 0, product: { id: 1, name: 'Coffee', description: 'Coffee Grounds from Ethiopia', price: 9 }, count: 1 }
const item2 = { id: 1, product: { id: 2, name: 'Tea', description: 'Oonlong Tea from China', price: 10 }, count: 5 }
const item3 = { id: 2, product: { id: 3, name: 'Bottled Water', description: 'Bottled Water from US', price: 2 }, count: 30 }

shoppingCart.upsertItem(item1);
shoppingCart.upsertItem(item2);
shoppingCart.upsertItem(item3);
console.log(shoppingCart.getTotalPrice()); //Expected Result: 119
item3.product.name = 'Himilayan Water';
item3.product.price = 10;
shoppingCart.upsertItem(item3);

console.log(shoppingCart.getItemsCount()); //Expected Result: 3
console.log(shoppingCart.getTotalPrice()); //Expected Result: 359
shoppingCart.removeItemById(1);
console.log(shoppingCart.getItemsCount()); //Expected Result: 2
console.log(shoppingCart.getTotalPrice()); //Expected Result: 309
```
## QUESTION 2
```question2.js
class Subject{
    observers ={};
    on(event, fn){
if(event in this.observers){
    this.observers[event].push(fn);
}
else{
    this.observers[event] = [fn];
}
    }
    emit(event ,message){
for(const fnc of this.observers[event]){
    fnc(message);
}
    }
}


const subject = new Subject();
subject.on('eat', console.log); // register an observer
subject.on('study', console.log); // register an observer

function foo(msg) {
    console.log('foo: ' + msg);
}

subject.on('eat', foo);
subject.on('study', foo);

subject.emit('eat', 'Corn');
//output for Line above: subject.emit('eat', 'Corn');
// Corn
// foo: Corn
subject.emit('study', 'cs445');
//output for Line above: subject.emit('study', 'cs445');
// cs445
// foo: cs445
```
