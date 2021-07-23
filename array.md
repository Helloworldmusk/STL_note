only note what I am not ensure;

```
template < class T, size_t N > class array;
```

arrays have a fixed size and do not manage the allocation of its elements through an allocator

 swapping two array containers is a linear operation that involves swapping all the elements in the ranges individually, which generally is a considerably less efficient operation. On the other side, this allows the iterators to elements in both containers to keep their original container association.

[**size**](https://www.cplusplus.com/reference/array/array/size/)

Return size (public member function )

The size of an array object is always equal to the second template parameter used to instantiate the [array](https://www.cplusplus.com/array) template class (`N`).

```cpp
  std::array<int,5> myints;
  std::cout << "size of myints: " << myints.size() << std::endl;
  
  size of myints: 5
```

**size vs max size**

The `max_size` of an array object, just like its `size`, is always equal to the second template parameter used to instantiate the array template class.

is same;



[**data**](https://www.cplusplus.com/reference/array/array/data/)

Get pointer to data (public member function )

Returns a pointer to the first element in the [array](https://www.cplusplus.com/array) object.

[**fill**](https://www.cplusplus.com/reference/array/array/fill/)

Fill array with value (public member function )

Sets *val* as the value for all the elements in the [array](https://www.cplusplus.com/array) object.

```cpp
// array::fill example
#include <iostream>
#include <array>

int main () {
  std::array<int,6> myarray;

  myarray.fill(5);

  std::cout << "myarray contains:";
  for ( int& x : myarray) { std::cout << ' ' << x; }

  std::cout << '\n';

  return 0;
}

//output myarray contains: 5 5 5 5 5 5
```



[**swap**](https://www.cplusplus.com/reference/array/array/swap/)

Swap content (public member function )

Exchanges the content of the array by the content of *x*, which is another [array](https://www.cplusplus.com/array) object of the same type (including the same size).



[**get (array)**](https://www.cplusplus.com/reference/array/array/get/)

Get element (tuple interface) (function template )

Returns a reference to the *I*th element of [array](https://www.cplusplus.com/array) *arr*.

```
template <size_t I, class T, size_t N> T& get (array<T,N>& arr) noexcept;
template <size_t I, class T, size_t N> T&& get (array<T,N>&& arr) noexcept;
template <size_t I, class T, size_t N> const T& get (const array<T,N>& arr) noexcept;
```

Position of an element in the array, with 0 as the position of the first element.
[size_t](https://www.cplusplus.com/size_t) is an unsigned integral type.

return : A reference to the element at the specified position in the array.

```cpp
// arrays as tuples
#include <iostream>
#include <array>
#include <tuple>

int main ()
{
  std::array<int,3> myarray = {10, 20, 30};
  std::tuple<int,int,int> mytuple (10, 20, 30);

  std::tuple_element<0,decltype(myarray)>::type myelement;  // int myelement

  myelement = std::get<2>(myarray);
  std::get<2>(myarray) = std::get<0>(myarray);
  std::get<0>(myarray) = myelement;

  std::cout << "first element in myarray: " << std::get<0>(myarray) << "\n";
  std::cout << "first element in mytuple: " << std::get<0>(mytuple) << "\n";

  return 0;
}
```

Output:

```cpp
first element in myarray: 30 
first element in mytuple: 10
```



