---
title: "Breaking Out Of Nested PHP Loops"
date: "2014-03-17"
categories: 
  - "php"
tags: 
  - "php"
  - "programming"
---

I came across a snippet of handy information today regarding nested PHP control structures and breaking out of them from within the structure at any level. Although the example is not important, I thought I'd use my exact use case as opposed to using the same old 'Foo, Bar' examples.

## My Example

I am currently working on my own PHP Framework, more as a learning curve than anything else, and came to the point at which the code would look at the URL and load the class and method being requested?—?or a default if the requested is not found.

```

// Previous code grabs the URL and breaks the '/page/request/' into an array
if ( !empty($_array_request_uri) && !empty($_array_request_uri[0]) ) {
    foreach ($_array_request_uri as $key => $value) {
	// Here we have entered the 1st Control Structure (foreach)
        switch ($key) {
            // And here we enter the 2nd Control Structure. (switch)
            case '0':
                if (class_exists($value)) {
                    $load_class_name = $value;
                }else{
                    break 2;
                }
                break;
            case '1':
                if (method_exists($load_class_name, $value)) {
                    $load_method_name = $value;
                }else{
                    break 2;
                }
                break;
            default:
                break;
        }
    }
}
```

So in the example above, if the requested class does not exist on the first for each loop?—?the switch statement's '0' case?—?then I don't want it to continue the for each looking for the requested method?—?the switch statement's '1' case. In that instance I want to break out of both the switch and the for each loop. And so just as when breaking out of a control structure by using `break;`, we can exit both the switch and for each loop simply by adding the number of levels deep we are after the break. e.g. `break 2;`.
