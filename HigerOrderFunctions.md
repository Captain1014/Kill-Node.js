## Higher Order Functions


Question 1 (1 point)
What is the output of the following function?
=====
function compose(f, g) {
const s = "composing";
const h = function(x) {
console.log(x);  
 f(g(x));
};
return h;
}
const frankenstein = compose(console.log, Math.sqrt);
frankenstein(9);

Question 1 options:

9
9

9
3 ✅

3
3

3
9

no output

error because some operation is not supported by the supplied type(s) - TypeError

error because an attempt is being made to access a variable that is not defined - ReferenceError

⭐️ Question 2 (1 point)
A [ ] is an object that conists of a function and the environment that it was created in...
class?
answer: closure

Question 3 (1 point)
Choose the term that most accurately and specifically describes the code below:
=====
(x) => x + 1;

Question 3 options:

function

function declaration

function expression

arrow function ✅

invalid syntax

Question 4 (1 point)
What's the output of the code below (error or no output are possible)?
=====
const names = ['Alice', 'Bob', 'Carol'];
names.forEach((n) => {console.log(`Hello ${n}`);});

Question 4 options:

Hello ['Alice', 'Bob', 'Carol']

['Alice', 'Bob', 'Carol']

Hello Alice
Hello Bob
Hello Carol ✅

Alice
Bob
Carol

ReferenceError (identifier not yet created or variable not in scope / inaccessible)

no output

Question 5 (1 point)
In the code below, what is the type of f?
=====
const f = function() {};

Question 5 options:

undefined

null

number

string

boolean

object ✅

Question 6 (1 point)
What's the output of the code below (error or no output are possible)?
=====
const numbers = [NaN, NaN, 100];
const mappedResult= numbers.map(isNaN);
console.log(mappedResult);

Question 6 options:

[true, true, false] ✅

[false, false, true]

[NaN, NaN, 100]

ReferenceError (identifier not yet created or variable not in scope / inaccessible)

no output

Question 7 (1 point)
What's the output of the code below (error is possible)?
=====
logWithPrefix('languages', 'Go', 'Ada', 'F#');
function logWithPrefix(first, ...args) {
console.log(first, args);
}

Question 7 options:

languages [ 'Go', 'Ada', 'F#' ] ✅

languages Go

ReferenceError (identifier not yet created or variable not in scope / inaccessible)

invalid syntax

⭐️ Question 8
Choose the term that most accurately and specifically describes ...args below:
=====
function fn(a, b, c, ...args) { }

Question options:

invalid syntax

the arguments variable

the spread operator

the rest operator ✅

Question 9 (1 point)
What's the output of the code below (error is possible)?
=====
const arr = ['1', '1', '0', '0'];
console.log(parseInt(arr.reduce((s, cur) => s + cur, ''), 2));

Question 9 options:

ReferenceError (identifier not yet created or variable not in scope / inaccessible)

TypeError

['1', '1', '0', '0']

1100

12 ✅

explanation: parseInt('1100',2) is parsing the string '1100' as a binary number.

Question 10 (1 point)
What is the output of the following function?
=====
function cachify(f) {
const cache = {};
return function(x) {
if(cache.hasOwnProperty(x)) {
return cache[x];
} else {
const res = f(x);
cache[x] = res;
return res;
}
};
}
const cachedSquare = cachify(function(n) { return n \* n; });
const res = cachedSquare(8);
console.log(res);

Question 10 options:

64 ✅

8

{}

undefined

no output

error because some operation is not supported by the supplied type(s) - TypeError

error because an attempt is being made to access a variable that is not defined - ReferenceError

Question 11 (1 point)
What is the output of the following function?
=====
function cachify(f) {
const cache = {};
return function(x) {
if(cache.hasOwnProperty(x)) {
console.log('cache hit');
return cache[x];
} else {
const res = f(x);
cache[x] = res;
console.log('updated cache');
return res;
}
};
}
const cachedSqrt = cachify(Math.sqrt);
cachedSqrt(16);
cachedSqrt(9);
cachedSqrt(16);

Question 11 options:

4
3
4

cache hit
updated cache
cache hit

cache hit

updated cache
updated cache
cache hit ✅

no output

error because some operation is not supported by the supplied type(s) - TypeError

error because an attempt is being made to access a variable that is not defined - ReferenceError

⭐️ Question 12 (1 point)
What's the output of the code below (error is possible)?
=====
const stringy = ['1', '10', '100'];
const reducedResult = stringy.reduce(secret, 1);
console.log(reducedResult);
function secret(product, ele) {
return product \* parseInt(ele, 2);
}

Question 12 options:

ReferenceError (identifier not yet created or variable not in scope / inaccessible)

'100'

1000

8

2 ✅

explanation: parseInt(1,2) is 1.
stringy.reduce(secret,1)

> the reduce method is called on the stringy array. The secret function is used as the callback, and '1' in reduce is passed as 'product' value
> stringy arr's element is passed as 'ele'
> after one turn, the secret function returns '1'
> in the second turn, the product value is '1' (the returned value)
> the ele is '10' now
> parseInt('10',2) is 2
> ...
> parseInt('100',2) is 8
> the final return value is 8
