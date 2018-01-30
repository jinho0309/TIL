## 하노이 타워
하노이 타워의 반복 패턴은 다음과 같다.
1. n-1개를 A에서 B로 옮긴다.
2. 맨밑에 원반 n을 A에서 C로 옮긴다.
3. n-1개를 B에서 C로 옮긴다.
재귀함수를 이용할 때는 문제이 반복 패턴을 찾고, 결국 n개의 문제를 1개의 문제가 해결되는 과정을 거쳐서 문제를 푼다.
```cpp
void hanoitower(int num, char from, char by, char to){
  if(num==1)
  1개면 단순히 A에서 C로 옮기면됨.
  else{
    hanoitower(n-1,from,to,by) //n-1개를 A에서 C를 거쳐 B에 가져다 놓는다.
    cout<<맨밑에 있는 n을 from에서 to로 옮기면됨.
    hanoitower(n-1,by,from,to) //B에있는 n-1개를 A를 거쳐 C에 가져다 놓는다.
  }
}
```
