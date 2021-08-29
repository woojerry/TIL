## CRA TypeScript로 하기 

```
npx create-react-app my-app --template typescript
or (my-app은 프로젝트명)
yarn create react-app my-app --template typescript
```

## 자동정렬 
> VSCode에서 .tsx file에서는 Prettier를 통한 자동정렬이 되지 않는 문제가 발생했다.
- 다음을 VScode의 setting.json에 추가했다.
```
"[typescriptreact]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
},
```

## 확장자
- ```.TypeScript```를 사용 할때는 ```.ts```, ```React 컴포넌트```의 경우에는 ```.tsx``` 확장자를 사용한다.

## Styled-components
- ```npm i styled-components @types/styled-components``` 명령어로 설치
