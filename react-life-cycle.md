### class life cycle
#### mount
1. state, context, defaultProps 저장
2. componentWillMount
3. render
4. componentDidMount

#### props update
1. componentWillReceiveProps
2. shouldComponentUpdate
3. componentWillUpdate
4. render
5. componentDidUpdate

#### state update
1. shouldComponentUpdate
2. componentWillUpdate
3. render
4. componentDidUpdate

#### unmount
1. componentWillUnmount

#### error
1. componentDidCatch

#### 16에서 추가
- getDerivedStateFromProps
    - props 변경에 따라 state도 변경

#### 17버전 deprecated
- componentWillMount
- componentWillUpdate
- componentWillReceiveProps


### function
#### useEffect
- componentDidMount, componentDidUpdate의 역할
- return으로 componentWillUnmount 역할