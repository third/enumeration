Enumeration
===========

A javascript-based implementation of Enumeration Type.


  - For array of strings, the value of the items in the enumeration starts with zero (0) and increments by one for the succeeding items. To override the start value, set *startAt* property of the *options* (optional) parameter. 
  - Each enumeration item has a function *.toStringValue()* which by default returns a capitalized string of the enumeration key. To customize string value, instantiate enumeration with an array of objects.

  - Accepted Parameters
    - Array of Strings ['Element0', 'Element1', .., 'ElementN']
    - Array of Objects [{Element0: 100}, {Element1: 200}, .., {ElementN: X}]
    - Object {Element0: 100, Element1: 200, .., ElementN: X}


Installation
------------

via npm:

    $ npm install enumeration

Examples
--------

**Require enumeration module**

    var Enumeration = require('enumeration');

**3 Ways to instantiate enumeration**

**1. Array of strings**

By default, the value of the first item is zero (0). Each successive item's value is increased by 1. To override the default start value, set the *startAt* property of the options parameter to your desired value (e.g. {startAt: 1}). 

Each enumeration item has a function called *.toStringValue()* which by default returns a capitalized string of the enumeration item. To specify custom string values, pass an array of objects (*see second way to instantiate*). 

        
        
*Syntax*
    
    new Enumeration(arrayOfStrings, [options])


*Sample Code*

    //create enumeration with array of strings    
    var Colors = new Enumeration(['RED', 'GREEN', 'BLUE']);

    //returns 0
    Colors.RED

    //returns 2
    Colors.BLUE

    //override default start value
    var Colors = new Enumeration(['RED', 'GREEN', 'BLUE'], {startAt: 1});

    //returns 1
    Colors.RED

    //returns 3
    Colors.BLUE
  
    //returns "Green"
    Colors.GREEN.toStringValue();

  
**2. Array of objects**

To specify custom string values, add a property named *stringValue* to each item in the array of objects

*Syntax*
    
    new Enumeration(arrayOfObjects)


*Sample Code*

    //create enumeration with array of objects
    var Colors = new Enumeration([{RED: 0}, {GREEN: 1}, {BLUE: 2}]);

    //returns 1
    Colors.GREEN    

    //returns "Green"
    Colors.GREEN.toStringValue();


    //specify custom string values
    var Colors = new Enumeration([{RED: 0, stringValue: 'Red Roses'}, {GREEN: 1, stringValue: 'Green Light'}, {BLUE: 2, stringValue: 'Blue Book'}]);

    //returns "Green Light"
    Colors.GREEN.toStringValue();


**3. Object**

If you have created your own javascript enumeration before, chances are this is the format that you are more familiar with.

*Syntax*
    
    new Enumeration(object)

*Sample Code*

    //create enumeration with object
    var Colors = new Enumeration({RED: 0, GREEN: 1, BLUE: 2});

    //returns 1
    Colors.GREEN

    //returns "Green"
    Colors.GREEN.toStringValue(); 



**Methods**

    //create enumeration with specified custom string values
    var Colors = new Enumeration([{RED: 0, stringValue: 'Red Roses'}, {GREEN: 1, stringValue: 'Green Light'}, {BLUE: 2, stringValue: 'Blue Book'}]);

    //returns "Blue Book"
    Colors.getStringValue(2);


    //if value is not found, specify a default value. This will return "Unknown"
    Colors.getStringValue(-1, 'Unknown');


    //check if value exists on the enumeration. This will return false.
    Colors.hasValue(99);


    //returns enumeration keys in an array ["RED", "GREEN", "BLUE"]
    Colors.getKeys();


    //returns enumeration values in an array [0, 1, 2]
    Colors.getValues();

    //returns enumeration string values ["Red Roses", "Green Light", "Blue Book"]
    Colors.getStringValues();


**Others**

    //returns {"RED":0,"GREEN":100,"BLUE":200}
    JSON.stringify(Colors);


