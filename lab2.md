# LAB 2 SOLUTIONS
## QUESTION 1

```typescript
class University{
    name: string;
   dept: string;
    constructor (name: string, dept: string){
        this.name = name;
        this.dept = dept;
    }
    graduation(year: number): void{
        console.log(`Graduating ${this.dept} ${year} students`);

    }
}
let miu: University = new University("MIU", "MSD");
miu.graduation(2021);
```
## QUESTION 2
```typescript
let bankAccount: {
   money: number,
    deposity (value: number): void 
};
bankAccount ={
    money: 2000,
    deposity(value){
        this.money +=value;
    }
};

let myself: {
    name : string,
    bankAccount: typeof bankAccount,
    hobbies: Array<string>,

};
myself ={
    name: "John",
    bankAccount: bankAccount,
    hobbies: ["Violin", "Cooking"],
};
myself.bankAccount.deposity(3000);
console.log(myself);
```
## QUESTION 3
```typescript
class Car{
    name: string;
    acceleration: number;
    constructor(name: string){
this.name = name;
this.acceleration = 0;

    }
    honk(): void{
console.log(`${this.name} is saying: Tooooooo!`);

    }
    accelerate(speed: number): void{
        this.acceleration = this.acceleration + speed;
    }
}
let car: Car = new Car("BMW");
car.honk();
console.log(car.acceleration);
car.accelerate(60);
console.log(car.acceleration);
```
## QUESTION 4
```typescript
let baseObjet: {
    width: number,
    length: number
};

baseObjet ={
    width: 0,
    length: 0
};
let rectangle: any = Object.create(baseObjet);
rectangle.width = 5;
rectangle.length = 2;

rectangle.calcSize = function(): number{
    return this.width * this.length;
};

console.log(rectangle.calcSize());
```
