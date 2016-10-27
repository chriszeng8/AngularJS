http://stackoverflow.com/questions/14502006/working-with-scope-emit-and-on
###$broadcast,$on and $emit,$on

First of all, parent-child scope relation does matter. You have two possibilities to emit some event:
`$broadcast` -- dispatches the event downwards to all child scopes,
`$emit` -- dispatches the event upwards through the scope hierarchy.

In the following examples, the scope `firstCtrl` is parent of the `secondCtrl` scope.

* broadcast variable from parent scope to child scope controller. 

```
function firstCtrl($scope)
{
    $scope.$broadcast('someEvent', [1,2,3]);
}

function secondCtrl($scope)
{
    $scope.$on('someEvent', function(event, mass) { console.log(mass); });
}
```

* emit variable from child scope to parent scope controller. 

```
function firstCtrl($scope)
{
    $scope.$on('someEvent', function(event, data) { console.log(data); });
}

function secondCtrl($scope)
{
    $scope.$emit('someEvent', [1,2,3]);
}
```