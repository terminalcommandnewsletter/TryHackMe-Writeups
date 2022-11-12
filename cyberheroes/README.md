# Cyber Heroes
## TCN | Sep 8 2022

## Enumeration in the browser
This has a fail but this will show my process.

Viewing the source code of the index page gives us nothing useful

Viewing the source code of the login page gives us the answer

## Analysing the vulnerable function

Let's analyse the authenticate function in the source code
```js
function authenticate() {
      a = document.getElementById('uname')
      b = document.getElementById('pass')
      const RevereString = str => [...str].reverse().join('');
      if (a.value=="[VALUE1]" & b.value==RevereString("[VALUE2]")) { 
        var xhttp = new XMLHttpRequest();
        xhttp.onreadystatechange = function() {
          if (this.readyState == 4 && this.status == 200) {
            document.getElementById("flag").innerHTML = this.responseText ;
            document.getElementById("todel").innerHTML = "";
            document.getElementById("rm").remove() ;
          }
        };
        xhttp.open("GET", "RandomLo0o0o0o0o0o0o0o0o0o0gpath12345_Flag_"+a.value+"_"+b.value+".txt", true);
        xhttp.send();
      }
      else {
        alert("Incorrect Password, try again.. you got this hacker !")
      }
    }
```
More over, focus on the 4th line
If a (the username as seen by the declaration of variables) is equal to [VALUE1] and b (the password as seen by the declaration of variables) is equal to reversed value of [VALUE2]

Either we could type these values in or directly open the text file linked subbing in the right values.

If we login, we get the message:

```
Congrats Hacker, you made it !! Go ahead and nail other challenges as well :D
    flag{ed____________________________6e} 
```