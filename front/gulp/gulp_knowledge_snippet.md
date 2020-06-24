# Gulp Basic

-   [GULP KNOWLEDGE](#GULP-KNOWLEDGE-SNIPPET)

>
> 해당 블로그의 글은 공부를 하면서 정리를 한 내용입니다.  
> 필자가 미처 모르는 부분이 있거나 잘못된 내용이 있을 수 있습니다.  
> 오타 및 잘못된 내용 발견 시, 
> 댓글로 남겨주시면 수정 및 반영하겠습니다.
> 감사합니다.  
> 내용은 추가되거나 수정될 수 있습니다
> 
> > 2020.06.24 작성
>

![](https://user-images.githubusercontent.com/40539864/85418072-4fbc5880-b5ab-11ea-959c-675ad35524df.jpg)

## GULP KNOWLEDGE SNIPPET

1. gulpfile의 파일은 자바스크립트를 이용하여 작성

2. gulpfile.js , Gulpfile.js gulp-cli에서 자동으로 인식한다

3. transplier 사용가능

4. gulpfile.js 폴더 형성을 통하여 코드 스플리팅이 가능하다.
진입파일은 index.js 
> transpiler를 사용하면 거기에 맞게 폴더 파일 이름 거기에 맞게 변환시켜 줘야한다.
> 예를 들어, typescript면 다 ts를 붙여서.. gulpfile.js > gulpfile.ts 

5. task를 크게 public task , private task로 나뉜다. 

6.  - 순차 task => series api
    - 병행 task => parallel api
    - 혼용가능 

7. 동적으로 조건에 따라 task 구성을 다르게 할 수 있다.
process.env.NODE_ENV에 같은 명령에 task를 다르게 돌릴 수 있다. 

8. gulp는 기본적으로 동기 task를 지원안함
> async, await을 사용하면 동기적 비슷하게 코드를 작성 및 사용가능

9. src API는 처음 파일 탐색 및 파이프라인 중간에 파일을 추가할 수 있다. 
추가된 파일은 변환이 이루어져야 사용할 수 있다. 
중간 파일 추가는 트렌스 파일링을 한 파일과 순수자바스크립트 파일과 합칠 때 많이 사용. 

10. src api 3가지 모드를 실행시킬 수 있다. 
- streaming 
    - 메모리 상으로 작업하기에 적합하지 않은 큰 파일들을 작업할 때 사용. (영상, 이미지)
    - 한번에 파일을 로드하지 않고 작은 chunck로 조금씩 stream하여 가져옴 
    - 플러그인은 적은 편
- buffered
    - 해당 api의 기본 모드
    - 메모리에 파일을 로드하여 작업
    - 대부분의 플로그인들은 대부분 해당 모드(버퍼 모드)일 때만 지원 
- empty
    - 파일을 로드하여 작업하지 않고 
    - 파일의 메타데이터(metadata)로만 작업할 경우 유용

11. glob : 파일 경로를 매칭하는데 사용되는 와일드카드 문자 및 문자열

12. globbing : 한개 및 그 이상의 glob을 사용하여 파일시스템에서 매칭되는 파일을 찾는 행동 

13. glob의 separator '/' 
window상에서 separator '\\\\'
그래서 window separator의 경우 glob 문자열에서는 escape가 이루어져 '/'가 된다
윈도우에서 node 구분자도 같기 때문에, node path method를 사용하지 말기
> __dirname, __filename, process.cmd()도 마찬가지 

14. src api에 탐색되는 파일이 매칭되는 파일이 아무것도 없으면 error가 발생함. 

15. negative glob(!)는 glob array에서 반드시 non-negative globs 다음에 나와야 한다

16. `!node_modules/**/*.js` 와 `!node_modules/**`는 차이가 있는데, 
전자는 해당 negative glob에 해당하는 폴더에 있는 파일들이 매칭이 되는게 있는지 다 찾기 때문에 탐색 시간이 걸리고 *globbing library* 가 최적화 할 수 없음. 
후자는 해당 폴더의 모든 하위 폴더 및 파일을 탐색 영역에서 제외시킴 

17. glob들 사이에서 탐색 시 중첩되는 파일이 있을 경우, 단일 src api 호출안에서는 
glup이 알아서 중첩부분을 제거하는 등의 최적화를 해준다. 
하지만 따로 chaning method로 또 src api가 호출되고 같은 파일이 탐색된 경우에는 중복된 파일의 제거가 이루어지지 않으니 참고. 

18. inline plugin 으로 작성이 가능.
    - 따로 task를 구성할 필요가 없을 때( 다른 곳에 쓰이지 않거나 )
    - 플러그 인을 만들거나 유지 관리가 필요 없을때
    - 플러그 인의 기능말고 추가기능이 더 필요할 때


