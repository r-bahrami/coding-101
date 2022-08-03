# some examples



### [Sequential Naming](https://github.com/m-bahrami/coding-201#variablesfilesfunctions-with-sequential-names-dynamically-variable-names)
```matlab
for i=1:3
    for j=1:2
    datalog.("foo"+i).("bar"+j) = i+j ;
    end
end
```
