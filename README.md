# demo

ES 2020 Features

globalThis context (this)
    console.log(window, this, self, frames, globalThis)
    In web workers only self will work
    In Node js we can't use windo object instead of that we can use global
    to utilize in all cases we can go with globalThis

promise.allSettled()
    Promise.all --> will execute with all resolved promises case, if any promised is rejected it will throw error and stops remaining execution
    Promise.allSettled --> will execute with mixed results of resolve and rejects

Nullis coalescing operator(??)
    to check the value other than null and undefined like '' and 0 kind of check will need to use this operator
    let x = {
        profile: {
            name: '',
            age: 0
        }
    }
    console.log(x.profile.name || 'jhon' , x.profile.age || 21) //jhon 21 "but it should be '' 0

    to resolve this issue we need to use ??

    console.log(x.profile.name ?? 'jhon' , x.profile.age ?? 21) //'' 0


Optional chaining operator(?.)

    if we don't have object properties in code and we're trying to access that property will get an error, to avoid that issue we try to add so many condition. To resolve thta issue we can user ?. operator

    let x = { }

    console.log(x && x.profile && x.profile.name);

    console.log(x?.profile?.name);

    *this operator will work with babel

BigInt
    


ES2021 Features

 String.prototype.replaceAll()
    replace will replace first occured instance replaceAll will replace in all occurences

 Promise.any()
    Promise.all([p1,p2,p3]) //wait for all -- abort if any reject
    Promise.race([p1,p2,p3]) //wait for all -- abort if first resolve or reject
    Promise.allSettled([p1,p2,p3]) //wait for all -- even though if any reject
    Promis.any([p1,p2,p3]) // wait for all -- abort on any first success

Logical asignment  (a||=1, b&&= c, c ?? = d)
    function add(a,b) { // if a is falsy value will be override if we use ||. For && if it value is truthy then override
        a = a || 0; // a || = 0
        b || (b=0); // b || = 0
        return (a+b)
    }

Week Ref and finalization Registry


    


* if you want to use input value as number directly without parsing it ===> document.querySelector("input").valueAsNumber and for date valueAsDate
* To remove duplicate values from array --> [...new Set(arr)]

* Injectors are two tpes 1. Module injector 2. component/template level injector "providers".




Observables vs promises


* Observables are lazy, when you subscribe then only executes... where as promise will excutes immediatley 

* Observables are cancalable 

* Observables can be sync and async, where as promises will be async

* Observables can emmit multiple values, promises can be with then catch and finally



App optimization techniques

* run out side Angular -- heavy scripts or 3rd party libraries

* detach view from change detection

* lazy load components via dynamic imports

* avoid many ngIfs and ngswtiches instead of these use dynamic components

* virtual scrolls for large set of list and server side pagination

Promises vs async await

 * code simplicty with async asnc await (clean code)
 * Error handling is easy in asyn await --> at block try catch we will have the error context instead of one more catch for promise
 * Conditional apis
 * Intermediat calls or dependent calls will be easy in asyn await ---> v1 = await result(); v2 = await result(v2)....
 * Debugging is easy with async and await








Sorting Algorithms

 * Bubble Sort
    Will do compare adjacent two elements and swap until we won't get any swappings

        for(i=0;i<arr.length-1;i++) {
            for(j=0;i<arr.length-i-1;j++) {
                if(arr[j]>arr[j+1]) {
                    swapArr(arr, j, j+1)
                }

            }
        }

* Quick Sort
    Quick sort and merge sort both are divide and conquer algorithm. In Quick sort will do with pivot based sorting

    Pivot can be start, middle or end index value based on that will sort lesser values to the left of pivot and remaining elements to right



    var quickSort = function(arr, low, high) {
        let i= low;
        let pivot = arr[high]
        for(let j= low; j<=high;j++) {
            if(arr[j]<=pivot) {                
                   swap(arr, i, j)
                i++;
            }
        }
        swap(arr, i+1, high)
        return arr;
    }

    var swap = function (arr, i, j) {
        [arr[i],arr[j]] = [arr[j],arr[i]]
    }


* Merge Sort
    Merge sort is same as quick sort for divide and conquer algorithm














currying with sum of n arguments

sum(1)(2)(3)(4).....(n)

function sum(a) {
    return function(b) {
        if(b) {
            return sum(a+b)
        } else 
        return a
    }
}
let sum = a=> return b=> return b ? sum(a+b) : a;



var user = {
    name: "anil",
    address: {
        personal: {
            city: 'hyderabad',
            area: 'vanastalipuram'
        },
        office: {
            city: 'hyderabad',
            area: {
                landmark: 'jubilihills Check post'
            }
        }
    
     }

}

var finalObj = {}
var keyName = 'user';
dProgram(user, key?) {
    var keysLength = Object.keys(user).length;
    if(keysLength) {
        var keyName = `keyName_'+key
        for(obj in user) {
            if(typeof(user[obj]) === 'string') {
                finalObj[`${keyName}_${obj}`] = user[obj]
            } else {
                dProgram(user[obj], obj)
            }
        }
    }
}


comments = [
    {
        _id:1,
        comment: "Sample",
        reply: 2
    },
    {
        _id:2,
        isReply: true,
        comment: "Reply sample1"
    },
    {
        _id:3,
        comment:"sample3"
    },
    {
        _id:4,
        comment: 'sample4',
        reply: 5
    },
    {
        _id: 5,
        isReply: true,
        comment: "reply for sample4"
    }

]


ondragover => preventdefault

ondrop => id= evet.dataTransfer.getData('text') draggableElement = document.getElementById(id) dropZone = evet.target dropZone.appendChild(draggableElement) event.dataTransfer.clearData()

ondragstart => event.dataTransfer.setData('text/plain', event.target.id)
<div maincontainer ondragover="" ondrop="">
    <div card id="" draggable="true" ondragsrat="">
</div>
<div maincontainer ondragover="" ondrop="op">
</div>






let arr = [[24,31], [12,14], [6,17], [28,50], [2,4], [44,49]]
// [24,50], [6,17], [2,4]

function arrInterSection(arr) {
    let length = arr.length;
    let result = []
    arr = arr.sort((a,b)=>{
        return b[0]-a[0]
    })
    // for(let i=0; i<length;i++) {
    //     let r1=arr[i][0], r2=arr[i][1];
    //     for(let j=0;j<length;j++) {
    //         if(arr[j][0]!== r1) {
    //             if(r1<arr[j][0] && r2>arr[j][0]) {
    //                 result.push([r1, arr[j][1]])
    //             }
    //         }

    //     }
    // }
    for(let i=0; i<length;i++) {
        let j=i++;
        if(j<length) {
            if(arr[j][0]<arr[i][0] && arr[j][1]>arr[i][0]) {
                result.push(arr[j][0],arr[i][1])
            }
        }
    }
    return result;
}

[44,49],[28,50],[24,31],[12,14],[6,7],[2,4]








/** React **/

Component Life Cycle
    Mounting:
        constructor()
        static getDerivedStateFromProps()
        render()
        componentDidMount()
    Updating:
        static getDerivedStateFromProps()
        shouldComponentUpdate()
        render()
        getSnapshotBeforeUpdate()
        componentDidUpdate()
    Unmounting:
        componentWillUnmount()
    Error Handling
        static getDerivedStateFromError()
        componentDidCatch()

    Other APIs: 

        setState()
        forceUpdate()

    Class Properties:

        defaultProps
        displayName
    
    Instance Properties:
        props
        state


/** RXjs **/

labrary to do asynchronus and event based programs by using observable sequences
Reactive Programming

Observable: represents the idea of invokable collection of future values of events
Observer: is a collection of callbacks that knows how to listen values delivered by the observables
Subscription: represents the execution of observable
Operators: are pure functions that enables functional programming to deal with collections with operations like map, filter 
Subject: is equalent to event emitter, and the only way to multicasting a value or event to multiple observers
Schedulers: are centralized dispatchers to control concurrency like setTimeout / requestAnimationFrame


Design patterns are nothing but re-usable designs and ineractions to resolve most complex design problems

The 23 Gang of Four patterns are generally considered as foundation for all patterns and these patterns mainly divided into three groups:
	1. Creational
	2. Structural
	3. Behavioral

##design patterns 

Most commonly used block of code need to be useful for creating a reusable object-oriented design for that we have few know practices to write your code. Patterns!! we have few design patters
Each design pattern focuses on a particular object-oriented design problem or issue

Main categories in design patterns

*Creational Design Patterns
	- Object creation will comes under this design pattern, which will take care of creating object
		- Constructor, Factory, Abstract, Prototype, Singleton and Builder

* Structural Design Patterns
	- Object composition and typically simple ways to realize relation between objects. limited effect on remaining object
		- Decorator, Facade, Flyweight, Adapter and proxy

* Behavioural Design Patterns
	- It foucs on flawless streaming communication between *disparate* Objects
		- Iterator, Mediator, Observer and Visitor


** Design Patterns Table ** 

Creational	  Based on the concept of creating an object.
    Class
      Factory Method	This makes an instance of several derived classes based on interfaced data or events.
    Object
      Abstract Factory	Creates an instance of several families of classes without detailing concrete classes.
      Builder	Separates object construction from its representation, always creates the same type of object.
      Prototype	A fully initialized instance used for copying or cloning.
      Singleton	A class with only a single instance with global access points.
 	 	 	 	 	 	 	 
  Structural	  Based on the idea of building blocks of objects.
    Class
      Adapter	Match interfaces of different classes therefore classes can work together despite incompatible interfaces.
    Object
      Adapter	Match interfaces of different classes therefore classes can work together despite incompatible interfaces.
      Bridge	Separates an object's interface from its implementation so the two can vary independently.
      Composite	A structure of simple and composite objects which makes the total object more than just the sum of its parts.
      Decorator	Dynamically add alternate processing to objects.
      Facade	A single class that hides the complexity of an entire subsystem.
      Flyweight	A fine-grained instance used for efficient sharing of information that is contained elsewhere.
      Proxy	A place holder object representing the true object.
 
  Behavioral	  Based on the way objects play and work together.
    Class
      Interpreter	A way to include language elements in an application to match the grammar of the intended language.
      Template
       Method	Creates the shell of an algorithm in a method, then defer the exact steps to a subclass.
    Object
      Chain of
      Responsibility	A way of passing a request between a chain of objects to find the object that can handle the request.
      Command	Encapsulate a command request as an object to enable, logging and/or queuing of requests, and provides error-handling for unhandled requests.
      Iterator	Sequentially access the elements of a collection without knowing the inner workings of the collection.
      Mediator	Defines simplified communication between classes to prevent a group of classes from referring explicitly to each other.
      Memento	Capture an object's internal state to be able to restore it later.
      Observer	A way of notifying change to a number of classes to ensure consistency between the classes.
      State	Alter an object's behavior when its state changes.
      Strategy	Encapsulates an algorithm inside a class separating the selection from the implementation.
      Visitor	Adds a new operation to a class without changing the class.

