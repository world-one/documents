### interface
#### interface 다중 확장
```
interface MapStateTypes {
  map: mapboxgl.Map;
  zoom: number;
}

interface MyInfoTypes {
  age: number;
  address: string;
}

interface PropTypes extends MapStateTypes, MyInfoTypes{
  name: string;
  index: number;

}
```


### Type Guard
- typeof
- instanceof
- in
- 사용자가 정의하는 방법