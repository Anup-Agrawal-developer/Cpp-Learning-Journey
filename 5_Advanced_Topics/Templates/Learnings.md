
Templates in C++ :-

It is a powerful tool which allows us to write generic and more readable code.
It enable us to define functions, classes and data structures that can operate with any data type.

- This avoids code duplication by keeping same function/Class/Structure for single value in
multiple data type way.

E.g.
without template

1. If we want to call a print function by passing string value or sometimes int value or
sometimes float value. Then it will look like below,

```
void Print(int value)
{
    cout<<value<<endl;
}

void Print(string value)
{
    cout<<value<<endl;
}

void Print(float value)
{
    cout<<value<<endl;
}

int main()
{
    Print(5);
    Print("Akash");
    Print(3.5f);  ==>  'f' is given to mention value as float specifically. If f is not written
    then compiler things it as double and then convert it into float which may do precision loss
}
```
Here to call same function with different data type. I have to create 3 different functions.

But, with templates,

templates allows us to use single parameter with different data type of capability as per
requirement.

E.g.

template<typename T>   ==> This is syntax to create template. Here our template name is T which
will use type in function parameter,
```
void Print(T value)
{
    cout<<value<<endl;
}

int main()
{
    Print(5);
    Print("Akash");
    Print(3.5f);
}
```
Now, because we have template T, as per parameter value template automatically defines datatype
respective to given value.

We can also check which typename is selected by template by using
```
typeid(decltype(enter_variable_name)).name()

For above example, cout<<"typename "<<typeid(decltype(value)).name()<<endl;
```
One more IMP point, semicolon should not be present after template declaration as it is not required.

if we print type for all 3 called functions it look like below,
```
Templates/build# ./Main
Calling templates [START]

[ Template Selected dataType:i, value:5 ]
[ Template Selected dataType:PKc, value:Akash ]
[ Template Selected dataType:f, value:3.5 ]

templates [END]
```
```
i stands for integer, PKc stands for char * and f stands for float.
```
We can also mention specific typename while calling functions like below
```
Print<int>(5);
Print<string>("Akash");
Print<float>(3.5f);

[ Template Selected dataType:i, value:5 ]
[ Template Selected dataType:NSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEE, value:Akash ]
[ Template Selected dataType:f, value:3.5 ]
```
```
NSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEE is for string
```
Note:- A function which has template parameter doesn't really exists for compiler. Compiler
check template functions only if they called from your program. You can also check and confirm
it by writing wrong syntax code inside Print then also compilation will work fine. But again
it depends upon compiler. Some compiler catches syntax error from template function and some not.
Specially, MSVC[Microsoft Visual Studio Code] won't recognise syntax errors for template
functions if they are not called from your program.
But, g++ or gcc means CLI compilers will recognise syntax errors for template functions even
it they are not called from your program.

One more thing, as we have initially created 3 seperate function with different type of
parameters. Templates also do same thing by using compiler. As templates is just Blue Print
not actual parameter.
At compile stage, if we have called
Print(5);  Compiler create Print defination function with int parameter instead of T.
Print(5.5f); Compiler creates one more Print defination function with float parameter instead of T.


We can also use templates for keeping constant values for int,float or string.

E.g.
```
template<int N>

class Array{
private:
    int arr[N];

public:
    void getSize()
    {
        return N;
    }
};

int main()
{
    Array<5> a;

    cout<<a.getSize<<endl;
}
```
Now, here we use template for keep array size value as int N.
Now, again this class will become blueprint as we used template inside class.
At compilation time, class with replaced value of N will be created if we create an object of that.
Like here for Array<5> a;
compiler creates new class,
```
class Array{
private:
    int arr[5];

public:
    void getSize()
    {
        return 5;
    }
};
```
We can also mentioned datatype of arr in template to make it fully generic like array<> of STL.
```
template<typename T, int N>
class Array{
private:
    T arr[5];

public:
    void getSize()
    {
        return 5;
    }
}
```
Now, it is just like array<> of STL.

Now, how we will use this Array,
```
like,  Array<int, 5> a;
or Array<string, 6> users_list;
```

Where we should use this templates fuctionality :-

1. Can be used in Locking Mechanisms.
2. Can be implemented for simpler logics. It will be easy to read and understand.
3. Can be used in mechanism systems.


When not to use templates :-

1. At very complex code logic. Templates will make it more complex and will difficult to
understand later.

