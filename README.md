
<div align="center">
<h1>simple pritning animation styles for python Project</h1>
</div> 


<h1> dvs_printf </h1>

[![PyPI Version](https://badge.fury.io/py/dvs-printf.svg)](https://badge.fury.io/py/dvs-printf)
[![Build Status](https://github.com/dhruvan-vyas/test_dvs_printf/actions/workflows/module_tests.yaml/badge.svg)](https://github.com/dhruvan-vyas/test_dvs_printf/actions)<br>
![Python Versions](https://img.shields.io/badge/python-3.10%20%7C%203.11%20%7C%203.12-blue)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/dhruvan-vyas/test_dvs_printf/blob/main/LICENSE)<br>
[![PEP8](https://img.shields.io/badge/PEP8-compliant-brightgreen.svg)](https://www.python.org/dev/peps/pep-0008/) 

***

# installation 

choose one liner command according to your system. <br>
Ensure that `pip` is installed and working on your system.

### **Linux / MacOS**
```bash
pip3 install dvs_printf 
```
```bash
python3 -m pip install dvs_printf
```

### **Windows**
```bash
pip install dvs_printf
```
```bash
python -m pip install dvs_printf
```
<br>



# Documentation

enhance way to handle console output for Python projects. 
The module offers `printf` style animation functions that designed to enhance the visual appearance of terminal-based Python projects,
Key features include different animation styles, customizable speeds, and flexible formatting options.

dvs_printf module include 3 main function and 1 sub function
* *[printf](https://github.com/dhruvan-vyas/dvs_printf#printf)* (core of the module)
* *[init](https://github.com/dhruvan-vyas/dvs_printf#dvs_printf.init)* (dynamic initializer for `printf`)
* *[showLoding](https://github.com/dhruvan-vyas/dvs_printf#dvs_printf.init)* 
* *[listfunction]()* 

# printf function 
The printf function allow users to apply various animation styles to their values. Supports different data types ***(string, int, float, list, set, tuple, dict)*** and classes ***(numpy, tensorflow, pytorch, pandas)*** as input. 
Users can choose from a range of animation styles, including typing, headlines, Center,Left,right and more. 
Customizable parameters include style, speed, interval, getmat, stay. 
``` python
from dvs_printf import printf

# defults
printf(values, style='typing', speed=3, interval=2, stay=True, getmat=False) 
```

### values
values stream can be anything like
`(string, int, float, list, set, tuple, dict)`
and you can give multiple input as any-data-type.
animation workd separately for each elemant given, 
and for each item in given list, set, tuple, dict.

```python              
printf(str, list, [tuple, set], dict, int, float,...)
```     

### style
style defins different types of print animation.
each style type works differently according to description below

``` python
style list: 
["typing", "headline", "newsline", "mid", "left", "right", 
"center", "centerAC", "centerAL", "centerAR", "f2b", "b2f", 
"gunshort", "snip", "matrix", "matrix2", "help"]
``` 

|  option  |                 description                  |
| -------- | -------------------------------------------- |
| typing   | print like typing animation                  |
| headline | print like head lines in news                |
| newsline | print running newslines animation            |
| mid      | print line from mid                          |
| left     | value coming from left side of the terminal  |
| right    | value coming from right side of the terminal |
| center   | values appear at center of the terminal      |
| centerAC | values arrang at center of the terminal      |
| centerAL | arrang list-item at center-Left on terminal  |
| centerAR | arrang list-item at center-Right on terminal |
| gunshort | firing the letters from short gun            |
| snip     | sniping the letters from end of the terminal |
| matrix   | print random letters to real line            |
| matrix2  | print 1st letter and 2nd random letters      |
| f2b      | typing and remove letter from back to front  |
| b2f      | typing and remove letter from front to back  |




### speed
Speed defins printf's animation speed, `defult speed is 3` 
you can set `speed from ( 1 to 6 )`
* 1 = *Very Slow*
* 2 = *Slow*
* 3 = *Mediam*
* 4 = *Mediam Fast*
* 5 = *Fast*
* 6 = *Very Fast*

```python
printf("hello world", speed=2) 
```


### interval
interval is waiting time between printing 
of two lines (interval in second) <br>
`defult interval is 2`, 
you can set interval from `0 to 5 or greater` 

``` python
printf("hello world", "hii, I am coder", interval=2)

#(with animation)
>>> hello world  
>>> # (wating time of interval time in second)
>>> hii, I am coder  
```


### stay
stay decides after style animation whether you want the `values on stream OR Not`.
stay can be True or False, `(defult stay = True)`.
if you want to remove printed line. you can set `stay=False`. 
So, After style amimetion and interval time printed Line can be removes.<br>

but some of the style `take No action on stay`,<br>
whether it is `True OR False`. it works as it should be.<br>
Ex. `(typing, headline, newsline, f2b, b2f, matrix, matrix2)`

``` python 
printf("hello world", 
    style="left", 
    stay=False,  #------> it's remove printed line after 1.5 seconds
    interval=1.5 #---------------------------------------^^^
    ) 

printf("hello world", 
    style="headline", #----------------------
    stay=True    # it's False by defult for headline
    ) 
```  
 
<br><br>


# dvs_printf.init Methrod


A dynamic initializer for printf that allows users to preset parameters for consistent usage.  
Priority order for settings parameters: printf's keywords > Setter Variables > dvs_printf.init's keywords > Defaults. <br>
more about on GitHub README.

`printf is inefficient to use for very-logn code.`
so you can `Use initializer for dvs_printf`, using `init method`
you can `pre set all parameters` with setter Veriavle.

```python
import dvs_printf 

# inistilizer
pf = dvs_printf.init()
printf = pf.printf

# perametars
pf.set_style = "centerAL"
pf.set_speed = 4
pf.set_interval = 0
pf.set_stay = False

printf("hello world", "wallcome to my project") 
```

*`dvs_printf.init`* is very dynamic function, 
you can `give defualt parameters in init` function
as wall as in `printf function.`

```python
import dvs_printf 

pf = dvs_printf.init(style="right")       # last priority 
printf = pf.printf

pf.set_style = "matrix"                   # second priority 

printf("hello world", style="headline")   # first priority           

printf("wallcome to my project")  # in this case style = "matrix" 
```
it works same `for all parameters.`
the `init` function has the `same keyword and defults` `as printf.`

as shown in this code-snippet we have `the dynemic init method`, 
we can `pre set all parameters` and can be `change at any point` according to your needs. <br>
`keywords inside printf` function has the most priority,
then Setter Variables `Ex. set_speed` has the second priority, and `keywords inside init` method has the thard priority and
if do not give init parameters it `works on defult parameters`.


* **priority of parameters**
    1. *printf's keywords*
    2. *setter Veriables*
    3. *dvs_printf.init's keywords*
    4. *the defults*
<br><br> 


# showLoding Function

```python
def showLoding(target: object,
    args: tuple | None = (),
    kwargs: dict | None = {},
    lodingText: str | None = "Loding ",
    lodingChar: str | None = "#"
) -> int: # [0 | 1]
```
```
Loding [##################           ] %60  
```
create loding bar in terminal with `threading` for 
* `waiting time for downlod files` 
* `run Any other function and wait till finish`
* `import other functions`
* `waiting for interner conection`

---

keep in mind that this function `already using print function` 
 so your `target function do not print anything` while loding 
otherwish loding bar will not work properly. <br>
loding funtion works on threading module 
so, it's `take same input as threading module`.
 

### target
the target `object` or `function` to work in background.<br>
the `object should be callable.` keep in mind that `target is keyword argument` 
not positional argument. it shuold be given as `target=function` and `do not call if for now`

```python
from dvs_printf import showLoding

def check_internet():
    # // Check for Interner Conection
    pass

showLoding(target=check_internet)
```

### args
the `positional arguments` that `target function taks` in `tuple`.
But if there is just one positional argument passing, add coma at the end, args=(1`,`) becouse `args should be Tuple`.
```python
def check_internet():
    # // Check Interner Conection
    pass
showLoding(target=check_internet)
```

### kwargs
`dictionary` of the `keyword arguments` that `target function taks.` <br>
`keywords in string` and `arguments in asked data-type.`

```     
    keyword    
       |       argument
       |           |
       ▼           ▼
,{  "number1":    10   , 
    "number2":   22.10 ,
    "name"   :  "A coder",  } 
```

### lodingText
text befor loding bar, you can change it according to you needs <br>
`defult is "loding "`

```
    lodingText = "downloading files"
        ▼
Downloding files[##########                   ] %35 
```

### lodingChar
Charactor to see progressed loding bar, `any charector` you can use in str <br>
```
    lodingChar = "*"
downloading files[**********                   ] %35   

downloading files[$$$$$$$$$$$$$$$              ] %50

downloading files[------------------           ] %60   
```



<br><br> 


# listfunction Function

An additionl function which is used by printf function, creats -> list[str] with input values 

```python
listfunction(*values: any, getmet: bool|str|None=False) -> list[str]
```


<!-- listfunction( ) takes `Any DataType` in input and return a new list.
created by input values & it break deta sets by index and add them into 
new list then return that list. -->

return list with each elements given. takes any DataType 
and gives `list[str]` with each elements by index. 
for `list, tuple, dict, set` breake this kind of 
DataSet and add Them into a list by index.

## getmat: 
matrix data modifier for 
`numpy, pytorch, tensorflow , pandas, list` 
it breaks matrices in `rows by index` and convet
that in to list of string, list[str]. <br>

getmat can be set as `True | "true" | "show"`, `default getmat = False`. 
* `True` or `"true"` to modify copy of matrix data for animation,
it's just show values of matrix 
* `"show"` matrix values `with information`, `<class, shape, dtype>` 
* if `getmat is False` it's apply animation `as normal matrix output`

<br>

```note
it's chake for truthy value (if getmat:)
So, "false" is True
```
<br>



```python
import tensorflow as tf
tf_array = tf.Variable([    # using (tf_array) Variable for this exemple
    [[1,1,1],
     [2,2,2],
     [3,3,3]],
], dtype=tf.float32)


from dvs_printf import printf    
pf = dvs_printf.init(style="left", interval=0.02)
printf = pf.printf              # printf used for animation


# ----------------------------------------------------------------------
# animation works with each element in output list, line by line: 

listfunction(tf_array, getmat=True)
# output_list: 
[
    '[1.0, 1.0, 1.0]', 
    '[2.0, 2.0, 2.0]', 
    '[3.0, 3.0, 3.0]'
] 


listfunction(tf_array, getmat="show")
# output_list: 
[
    '[1, 1, 1]', 
    '[2, 2, 2]', 
    '[3, 3, 3]', 
    "<class 'Tensorflow'",
    "dtype: 'float32' ",
    "shape: (1, 3, 3)>"
]


listfunction(tf_array, getmat=False)
# output_list: 
[
    "<tf.Variable 'Variable:0' shape=(1, 3, 3) dtype=float32, numpy=",
    "array([[[1., 1., 1.],",
    "        [2., 2., 2.],",
    "        [3., 3., 3.]]], dtype=float32)>"
]
```

