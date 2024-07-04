
##### Mock method
```
doReturn(result).whenever(objeck).getSomthing()
whenever(objeck.getSomthing()).thenReturn(result)
```
##### Типизированный any
```ArgumentMatchers.<ParameterizedTypeReference<Response<Long>>>any()```