
###Master the Scope of the Directives in AngularJS
* From [Mastering the Scope of the Directives by Shidhin](https://www.undefinednull.com/2014/02/11/mastering-the-scope-of-a-directive-in-angularjs/)

Sample Directive
```
var app = angular.module("test",[]);
app.directive("myDirective",function(){
    return {
        restrict: "EA",
        scope: true,
        link: function(scope,elem,attr){
            // code goes here ...
        }
    }   
 });
```

In a nutshell:

1.`scope: true` -> childscope which inherit all properties from parent scope, change properties of this scope does not affect parent scope.

2.`scope: false` -> same scope object as the parent scope, changing variable here will affec the parent scope.

3.`scope: {}` -> isolated scope which properties can be passed from parent scope via HTML DOM element definition. 
