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