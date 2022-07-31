

@testing-library/react


ts, next를 사용할 때, tsconfig를 추가해줘야한다.

jest.config.js
```
module.exports = {
  transform: {
    '^.+\\.[j|t]sx?$': `ts-jest`,
  },
  testEnvironment: 'jsdom',
  testRegex: '/__tests__/.*\\.(test|spec)\\.(t|j)sx?$',
  moduleFileExtensions: ['ts', 'tsx', 'js', 'jsx'],
  coveragePathIgnorePatterns: ['/node_modules/', '/__tests__/'],
  globals: {
    'ts-jest': {
      tsconfig: 'tsconfig.jest.json',
      diagnostics: true,
      isolatedModules: true,
    },
  },
```


tsconfig.jest.json
```
{
  "extends": "./tsconfig.json",
  "compilerOptions": {
    "jsx": "react"
  }
}

```