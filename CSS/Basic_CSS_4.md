## 모션그래픽
CSS의 최신버전에서는 포토샵이나 플래쉬와 같은 프로그램으로 해야 했던 일을 CSS로도 할 수 있게 되었다.
### 전환(transition)
전환은 효과가 변경되었을 때 부드럽게 처리해주는 CSS의 기능. 이와 관련된 것으로는 아래와 같은 속성들이 있음.
- ```transition``` : 장면 전환은 부드럽게 할 수 있는 기능
- ```property``` : 어떤 속성에 transiton을 적용할 것인지(all or 특정 속성(```transform```, ```font-size``` 등)
- ```duration``` : 몇 초에 걸쳐 전환할 것인지
- ```transition``` : 위의 두 개의 속성의 축약형(```transform 1s```, ```font-size 2s``` 이렇게 두 개 나눠서 적용도 가능)
- ```delay``` : 처음에 시간차를 두고 전환
- ```timing-function``` : 장면전환속도를 균일하지 않게([ceaser 사이트 참고](https://matthewlein.com/ceaser/))
## 유지보수
유지하고 보수하는 것이 편리하지 못하면 디자인을 과감하게 전개하는 것은 어려운 일. 따라서 일정한 규모의 사이트가 되면 유지보수를 효율적으로 해서 프로젝트의 복잡도를 낮추는 것은 정말 중요한 일. 대규모의 CSS 시스템을 구축할 때 필요한 여러가지 테크닉들을 알아보자.
### link와 import
외부로 파일을 빼는 방법은 크게 두가지
1. ```<link rel="stylesheet" href="style.css">```
2. ```<style>@import url("style.css")</style>```
## Library
### fontello
딩벳폰트는 폰트 대신 어떤 문자에 해당하는 이미지로 이루어진 폰트를 의미. fontello는 딩벳이나 아이콘을 폰트로 제공하는 여러 서비스를 모아둔 서비스. 특히 SVG 파일을 업로드하면 폰트로 만들어주기도 한다. [fontello](http://fontello.com/)
### buttons
디자인 된 간단한 버튼 CSS 라이브러리
- [Buttons 홈페이지](http://unicorn-ui.com/buttons/
