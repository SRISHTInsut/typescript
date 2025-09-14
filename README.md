# typescript
for sih project (Sheriyans)
---
- type handling which is not there in javascript
1. Type script Setup
- setting up a typescript project
- configuring tsconfig.json
- compiling typescript

- koi bhi valid javascript code is valid typescript code hai
- if errors honge toh errors display toh honge but since the file is converted into typescript errors aayenge which means though file is compiled usmai errors hai.
![alt text](image.png)
- tsc filename //fir compile hojayega
- har baar changes karke if compile na karna ho to run the command as:
tsc --watch

//Basic Types
- Primitive types (number, string, boolean)
- Arrays
- Tuples
- Enums
- Any, Unknown, Void, Null, Undefined, Never

//Primitive and reference
- primitive mai kahi bhi bracket nahi aata
- reference mai brackets include hote hai

- primitive ko copy kar sakte ho directly
- reference ko directly copy nahi kar sakte 
- ek array mai if number and string both hai toh typescript infers it stating ki wo (string | number) ka array hai. javascript ye feature nahi deti hai
- let arr = [1, 2, 3, "abcd"]
- niiche wali declaration ne constraint laga diya that the type will be restricted to number only.
- let arr: number[] = [1, 2, 3, 4, "abcd"];
- tuple declaration:
let arr2: [number, string] = [12, "hari"];

- Enums
enum UserRoles{
    ADMIN = "admin",
    GUEST = "guest",
    SUPER_ADMIN = "super_admin"
}

enum StatusCodes {
    ABANDONED = "abandoned status code 500",
    NOTFOUND = "not found status code 404"
}

- let a; //iska type since defined nahi hai thus set to any

- hume make sure karna hai ki type any na ho nhai toh what's the role of type script really?

- type narrowing
let a = unknown;
a = 12;
a = "hari";

if(typeof a === "string")
    a.toUpperCase();

- aesa fntn jo kuch return nahi kar raha waha aapko colon lagakar batana padega konsa type hai-> 

function abcd(): void {
    console.log("hari");
}

function abcd(): number {
    return 12;
}

- null
let a: null;

- union
let a: string | null;
a = "hari";
a = null;

- never is wsed when some piece of code ki execution ke baad kuch bhi execute na ho (error handling and infinite codes mai zaroorat padti hai rest it's rarely of use)
function abcd(): never {
    while (true) {}
}
abcd();
console.log("hey");

//Type inference
// Understanding type inference (automatically type assignment ke saath determine ho jata hai)
// type annotations (colon lagakar type define karna)

//Interfaces and Type Aliases
- Defining interfaces
- Using interfacses to define object shapes
- Extending interfaces
- Type aliasing
- Intersection types

- interface (basically for eg object ke liye deine kiya toh) konsi datatype values ayengi wo define karta hai
 interface User {
    name: string,
    email: string,
    password: string,
    gender?: string
 }

 const obj = {
    name: "hari",
    email: "hari@gmail.com",
    password: "abcd"
 }

 function abcd(obj: User) {}

 abcd(if yaha object with same interface as User pass nahi kiya toh error ayega);

 so, 
 abcd({name: "hari", email: "hari@gmail.com", password: "abcd"});
 //since gender field ke aage Question mark tha in interface so wo optional hai thus object mai if hum wo field pass nhi karenge toh bhi chalega, also if any field baakiyo mai se nhi pass kari toh bhi error and if extra pass kardi jo User interface mai nhi hai declared toh bhi error.

 abcd({name: "hari", email: "hari@gmail.com", password: "abcd", gender: "Female"});

 - extends in interface
 // matlab jaise if mujhe already defined interface ki toh saari properties chaiye hi plus kuch or fields bhi chahiye toh hum wo mention karenge in extends

 interface Admin extends User {
    admin: boolean;
 }

 // do interfaces of the same name are merged matlab if do interface define kare of same name but different properties toh while defining we will be able to access all the properties defined in the interfaces.

 // type aliasing mai basically hum types ko deine ek value mai store kar lete hai

 type value = string | number | null;
 let a: value;

 //how are type and interfaces diff?
 - interfaces with the same name were being merged but in type error aajati hai
 - type ka kaam hai type create karna using primitive yaani number, string etc
 - interface ka kaam hai object ka shape bnana

 //Classes & Objects
 - class definitions
 - Constructors
 - Access Modifiers (public, private, protected)
 - Read Only properties
 - Optional properties
 parameters properties
 - getters & Setters
 - Static members
 - Abstract classes and methods

 