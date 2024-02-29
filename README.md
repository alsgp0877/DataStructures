## DataStructures with using Javascript (2024/02/27 ~ )
<details>
  <summary> 2023-03-01 3장 1 연습문제
</summary>

  -  2장에서 자바스크립트에 내장된 반복자 함수를 사용해보려고 했으나 기억이 잘 나지도 않고 for과 if만 있다면 다 구현할 수 있다고 생각해서 하드코딩하였다.
  -  현재 리스트의 모든 요소보다 클때만 요소를 삽입하는 함수를 구현하고 숫자일때와 텍스트일때도 고려해야하는 문제였다.
  -  처음에는 숫자일때와 텍스트일때도 조건을 가야하니까 typeof 키워드를 사용하여 구분해야하나? 라고 생각했는데
  -  결국 텍스트들도 아스키코드에 의거하면 숫자로 변경되고 순차적으로 커지는 구조들이라 단순하게 크고 작음을 비교해도 결과가 나올것이라 생각하고 if문의 표현식을 정했고
  -  cnt의 경우 모든 요소를 비교해야하니 cnt의 값이 리스트의 요소수와 같다면 모든 수에 대한 조건이 성립이 된거다 라고 생각하고 코드를 짰다.

    ````
    function insertList(element){
      var cnt = 0;
      for(var i = 0; i<this.dataStore.length;i++){            
          if(this.dataStore[i] < element){
              cnt++;//현재리스트의 모든 요소보다 클때
          }
       }
      
      if(cnt == this.dataStore.length){
         this.append(element);
      }
    }

    ````

</details>

<details>
  <summary> 2023-02-29 3장 리스트
</summary>

  - 리스트는 저장할 데이터가 많지 않을때, 순서가 필요 없을때, 검색할 필요 없을때 사용한다고 한다.
  - 따로 검색을 해보니까 순차구조여서 계속해서 데이터가 쌓이는 구조이기때문에 양이 많아지고 검색을 하려면 첨부터 끝까지 다 찾아야 해서 그렇다고 한다.
  - 책에 있는 List 클래스 구현 예제를 참고한다.

</details>

<details>
  <summary> 2023-02-28 2장 연습문제
</summary>

  - 이차원 배열을 이용해 월간 온도 자료를 저장하도록 weeklyTemps 객체를 고치시오, 월간 평균, 지정한 주의 평균, 모든주의 평균을 출력하는 함수를 만드시오
    - 달력을 기준으로하면 예외처리할게 너무많으나 간단하게 연산만 되도록 코딩했다. 
    - 월간은 한달동안을 말하는것
    - 이차원 배열을 사용하려면 [[1주차],[2주차],[3주차],[4주차],[5주차]] 이런식으로 해야 계산이 알맞게 될 것 같았다.
    - week.add([1,1,1,1,1,1,1]); 과 같이 데이터를 입력한다고 가정한다. 이게 젤 쉬운 입력 방법이라고 생각함 ;;
    - 예제를 크게 벗어나지 않는 선에서 코딩했다. 있는것을 잘 사용하는것이 중요!

    ````
      function weekTemps(){
        this.dataStore = [];
        this.add = add;
        this.monthAverage = monthAverage;
        this.weeklyAverage = weeklyAverage;
        this.weeklySelectAverage =  weeklySelectAverage;
      }
      function add(tmp){
          this.dataStore.push(tmp);
      }
    
      function weeklyAverage(){
          var total = 0;
          var tmp = [];
          for (var i=0;i<this.dataStore.length;i++){
              for (var j=0;j<this.dataStore[i].length;j++){
                  total += this.dataStore[i][j];
              }
              console.log(i+1+"주차 평균"+ total/7);
              total = 0;
          }
      }
      
    
    function monthAverage(){
        var total = 0;
        for (var i=0;i<this.dataStore.length;i++){
            for (var j=0;j<this.dataStore[i].length;j++){
                total += this.dataStore[i][j];
            }
        }
        console.log("한달 평균"+ total/31)
    
    }
    
    function weeklySelectAverage(month){
        var total = 0;
        var tmp = [];
        for (var j=0;j<this.dataStore[month].length;j++){
            total += this.dataStore[month][j];
        }
        console.log(month+1+"주차 평균"+ total/7);
        total = 0;
    }

    ````

</details>

<details>
  <summary> 2023-02-27 2장 배열
</summary>

  - 자바스크립트로 배열을 만들땐 var numbers = [] 와 var numbers = new Array(); 이렇게 두가지가 있다. 
  - 문자열을 배열로 만드는것은 split() 함수 사용
  - 배열을 문자열로 만드는것은 join과 toString 함수 사용, 두개의 차이점은 구분자가 있고 없고 말곤 아직 잘 모르겠다.
  - 배열요소 자체에 접근하는건 깊은 복사, samenus = nums 같이 변수로만 할당하는것은 얕은 복사라고 한다. 아무래도 배열 요소 자체에 접근하는것은 주소와 값 자체에 접근하는것 같고 변수로만 할당하는것은 주소만 복사한것으로 보인다
  - indexOf() 함수는 인자로 문자열 요소를 주면 해당 인자가 있는 문자열일 경우 반환한다
  - 새 배열을 만드는 방법으론 concat과 splice가 있는데 concat은 기존배열 뒤에 추가해서 배열을 만드는것이고 split는 (3,3) 앞인자는 기존배열의 위치, 뒷인자는 기존배열에서 사용할 요소수인데 결과 값만큼 짤라서 새배열을 만들고 그렇게 짤린 배열또한 새로운 배열로 만들어져 총 2개의 결과를 확인 할 수 있음
  - 배열 맨앞이나 맨뒤에 추가하고 싶은 경우 push() pop() unshift() shift() 함수를 사용하고 배열 중간에 추가하고 싶은 경우 splice를 사용하면된다.
  - 배열 정렬시 reverse() 역방향 sort는 정방향인데 문자열만 되며 숫자를 하고 싶은 경우 인자로 정렬기준 함수를 넣어서 정렬할 수 있다.
  - 배열의 각각의 요소에 함수를 설정하고 싶은 경우 forEach 함수를 사용하고 거기에 새 배열을 만들어 내고 싶으면 map 함수를 사용한다.
  - filter() 함수도 새 배열을 반환하나 조건은 불린 함수를 만족하는 요소를 포함한다는 것이다.
  - 이차원 배열의 경우 내가 아는건 [i][j] 밖에 없어서 패스

</details>

## 참고자료
![image](https://github.com/alsgp0877/DataStructures/assets/71861051/893a30da-c781-4343-aea4-b1ef029a05b7)
