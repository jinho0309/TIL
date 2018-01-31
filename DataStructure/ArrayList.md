#연결리스트
## 리스트 자료구조의 ADT
- `void Init(List *list)`
- `void Insert(List *list, Item item)`
- `int First(List *list, Item *item)`
- `int Next(List *list, Item *item)`
- `int Remove(List *list)`
- `int Count(List *list)`
## 배열을 이용한 리스트
- 장점
  - 데이터의 참조가 쉬움. 인덱스 값을 기준으로 어디든 한 번에 참조가 가능.
- 단점
  - 배열의 길이가 초기에 결정되며, 변경이 불가능
  - 삭제의 과정에서 데이터의 이동이 자주 일어난다.
```cpp
void InitList(List* plist){
	plist->numOfItem = 0;
	plist->curPosition = -1;//왜 -1 부터 시작하지?
}
```
- 리스트를 초기화한다. 현재의 position을 -1로 설정하는 이유는 항상 num보다 작아야하니까
```cpp
void Insert(List* plist, Item item){
	if(plist->numOfItem>=LIST_LEN){
		cout<<"저장불가";
		return;
	}
	plist->arr[plist->numOfItem]=item;
	(plist->numOfItem)++;
}
```
- 리스트의 현재 갯수가 배열의 최대갯수를 넘을 수 없다.
- plist->numOfItem은 항상 아이템이 저장된 index의 다음을 가리키므로 numOfitem의 index에 item을 추가하고 numOfitem을 1증가 시킨다.
```cpp
int First(List* plist, Item* item){
	if(plist->numOfItem == 0)
		return FALSE;

	plist->curPosition=0;
	* item =plist->arr[plist->curPosition];
	return TRUE;
}
```
- 리스트의 현재 position을 0으로 설정한다. 그 이유는 리스트의 position을 0으로 재설정함으로써 데이터의 참조가 앞에서부터 다시 진행될 수 있도록 한다.
```cpp
int Next(List* plist, Item* item){
	if((plist->curPosition)>=(plist->numOfItem)-1)
		return FALSE;

	(plist->curPosition)++;
	* item = plist->arr[plist->curPosition];
	return TRUE;

}
```
- curPosition>=numOfItem-1은 그 다음에 참조할 아이템이 없다는 것을 의미.
```cpp
Item Remove(List* plist){
	int pos = plist->curPosition;
	int num = plist->numOfItem;
	Item item = plist->arr[pos];
	for(int i=pos;i<num-1;i++)
		plist->arr[i]=plist->arr[i+1];
	(plist->numOfItem)--;
	(plist->curPosition)--;

	return item;
}
```
- 처음과 마지막의 아이템이라면 상관없지만 중간의 아이템이 제거된다면 그 이후의 아이템들을 한칸씩 당겨와야 한다.
- curPosition에 1을 감소시키는 이유는 삭제로 인해 공간을 메우려 데이터를 한 칸씩 앞으로 이동시키면, 참조가 이뤄지지 않은 한칸 앞에있던 Item을 가리키게되므로 -1한다.
