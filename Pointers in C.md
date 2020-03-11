>One thing that you will learn about C, if you haven't already, is that legal does not necessarily imply correct, and correct now does not necessarily imply correct forever! Be careful.

## Dereferencing Operater " \* "

When you declare a pointer, you always write something like: `int *p`, and you are taught that it defines a pointer that points to an integer. 

It is not what it does. The statement `type x;` only anounces to the wold that variable `x` is of type `type`, in this case `*p` is an integer, not `p` is a pointer to an integer, because it only declares variables, not pointers.

And here is where asterisk(`*`) operator comes into play. It dereference a pointer to the variable that it points to. So instead of saying `p` is a pointer that points to an integer, we say `*p` is an integer. This way we don't mess up with the way declaration works. Similarly, `int **p` declares that `**p` is an integer, which implies `*p` stores the address of that integer and `**p` stores the address of the pointer that points to that integer. 

Pushing on a little, this understanding helps with the dreaded `const` qualifier.
While `const int a=1` means `a` is a constant integer and later `a=something` is not allowed, `int const *p` will declare a pointer and the value of the variable it points to cannot be changed. For example, with `int a=1; int const *p=&a;` you can't change the value of `a` by doing `*p=something`. However, you can change the value of `a` since it is not a constant, you just can't do it through `*p`. 

Up to now, the order of `int` and `const` doesn't matter, `int const` and `const int` are equivalent. The difference comes in when there is an `*` in between. 

 1.`int *const p` declares variable `p` is a constant and variable `*p` is not. For example, `int a=1;int *const p=&a;*p=3;` is fine, but `p=&b` is not allowed.    
 2. 'const int *const p` decalres variable `p` is constant and variable `*p` is constant as well. The pointer cannot be pointed to other variables and the variable it points to cannot change its value.

## A voild pointer can hold address of any type
We know a pointer to int must hold address of an int, a pointer to float must hold address of a float. However, there does exist a type of pointer that can hold address of any type, and it is voild pointer.
```
int x = 10;
void *p = &x;
```

A voild pointer are assignable to any other pointer type.
```
float y = 20.0;
void *p = &y;
float *pfloat;
pfloat = p;
```

A voild pointer can be returned by a function.
```
void* return_me(int* p){
    return *p;
}
```

## Howeverr, it can not be dereferenced
