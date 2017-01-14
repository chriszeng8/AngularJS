http://jsfiddle.net/maxisam/QrCXh/

http://stackoverflow.com/questions/16845605/is-it-possible-to-update-parent-scope-from-angular-directive-with-scope-true

So, the reason your fiddle doesn't work is because when a primitive type (i.e., a string, number, or boolean type) is written to -- e.g., scope.name = newName -- the "write" always goes to the local scope/object. In other words, the child scope gets its own name property that shadows the parent property of the same name. The fix is to use an object, rather than a primitive type, in the parent scope. The child scope will then get a reference to that object. Any writes to the object properties (whether from the parent or the child) will go to that one object. (The child scope does not get its own object.)

```
$scope.obj = {name: 'Dave'};
```

Then in your directive:

```
scope.obj.name = newName;
```

and HTML:

```
Hello, {{obj.name}}!
```
