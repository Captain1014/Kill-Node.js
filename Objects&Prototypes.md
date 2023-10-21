⭐️ Question 1 options:
console.log([1, 2, 3],[ ] Array);

What is the javascript keyword to check if an [1, 2, 3] was derived from an Array? (or specifically, an object was derived from a constructor?) Fill in the javascript keyword / operator in the blank. Hint: this is not a function - it's binary, infix operator.
answer: instanceof

Question 2 (1 point) 
 Saved
When we call 'toString()' on arrays like [1, 2], the Object.prototype.toString() method is called. Hint: try using the node interactive shell to find out!

Question 2 options:
	True
	False.✅


uestion 3 (1 point) 
 Saved
// What is the output of the code below?
// 

const numbers = [1, 2, 3, 4];
const numbersCopy = numbers.slice();
console.log('slice' in numbers);
console.log(numbers.hasOwnProperty('slice'));
Question 3 options:

true then true


true then false ✅


false then false


false then true


no output

error


Question 4 (1 point) 
A constructor's [[prototype]] (that is, the object that's searched for a property if the property doesn't exist on the constructor) is Function.prototype.

Object.getPrototypeOf(MyConstructor) === Function.prototype

Question 4 options:
	True ✅
	False

⭐️ Question 5 (1 point) 
 Saved
const numbers = [1, 2, 3, 4];
console.log(Object.getPrototypeOf(Object.getPrototypeOf(numbers)) === Object.prototype);
Question 5 options:
	True ✅
	False 

explanation: the chain of prototypes
https://i.stack.imgur.com/d4bDt.png


Question 6 (1 point) 
 Saved
Question 6 options:
The prototype of Object.prototype is
null

Question 7 (1 point) 
// what is the output of this code?

class Item{
    constructor(price) {
        this.price = price;
    }
    applyDiscount(discount) {
        this.price -= discount;
    }
}
class Shirt extends Item {
    constructor(price, size) {
        super(price);
        this.size = size;
    }
}
const s = new Shirt(16, 'Small');
s.applyDiscount(4);
console.log(s.price, s.size);

12 'Small;

⭐️ Question 8 (1 point) 
// What does this refer to when your invoke a function by using a regular 
// (consider strict mode)
// function call? For example:


function foo() {
    console.log(this);
}
Question 8 options:

the global object 


the object that the function was 'called on'


an object that this is explicitly set to by the caller


an "empty object" with no properties


undefined ✅

this code causes an error

explanation: "this" keyword
means -> the *object* that is executing the current function.
So in non-strict mode, it is 'the global object' but in strict mode, it's undefined.


⭐️ Question 9 (1 point) 
// What is the output of this code?
// (consider strict mode)

function User(username) {
    this.username = username;
}

User.prototype.save = function() {
    // assuming that saveToDatabase function exists
    saveToDatabase();
    console.log('saving ' + this.username);
};

const user = User('pizza4life');
console.log(user);
Question 9 options:

undefined


error ✅


no output


{username: pizza4life} 


{username: pizza4life, save:[Function]}



⭐️ Question 10 (1 point) 
// What does 'this' refer to when you invoke a function by using the
// keyword, new (that is, use a function as a constructor)? For example:
//

const obj = {x: 123, foo: foo};
function foo() {
    console.log(this);
}
const f = new foo();
console.log(f);
Question 10 options:

the global object


the object that the function was 'called on' 


an object that this is explicitly set to by the caller


an "empty object" with no properties ✅ (f)


undefined

this code causes an error


⭐️ Question 11 (1 point) 
const duck = {
    name:'Quincy',
    quack() {
        console.log('Quack!')
    }
};
const duckling = Object.create(duck);
console.log(`${duck.name},${duckling.name}`);
What does the above print?

Question 11 options:

Quincy,undefined 

undefined,Quincy

Quincy,Quincy ✅

throws ReferenceError

explanation: Object.create creates an object "duckling" that inherits from the duck object.


Question 12 (1 point) 
const numbers = [1, 2, 3, 4];
console.log(Object.getPrototypeOf(numbers) === Object.prototype);
Question 12 options:
	True
	False  ✅

