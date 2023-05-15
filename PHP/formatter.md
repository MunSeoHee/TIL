### prettier
#### plugin-php 설치
1. 콘솔에서 아래 디렉터리로 이동
```
cd ~/.vscode/extensions/esbenp.prettier-vscode-{버전}/
```
2. 설치
```
npm install @prettier/plugin-php
```
3. vscode settings.json에 추가
```
"[php]": {
    "editor.formatOnSave": true
},
```
4. .prettierrc 파일을 생성 및 옵션 세팅
    - 사용 가능한 옵션 : https://github.com/prettier/plugin-php
