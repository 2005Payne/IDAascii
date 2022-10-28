# IDAascii

## ===설명===
아이다에서 문제를 풀다보면   
![image](https://user-images.githubusercontent.com/88232976/198500304-d2fee6f2-7032-48a5-b4ff-510373e6c55f.png)   
이런 식으로 16진수들을 하나하나 아스키코드로 변환해야 될 때가 있는데   
그냥 저 메모리에 있는 숫자들을 하나하나 옮기지 않고 복사 붙여넣기 해서 사용하고 싶어 만들었다.   
(dup는 뒤에있는 16진수가 dup앞에 있는 숫자만큼 있다는 뜻이다   
ex) 3 dup(13h) == 13h, 13h, 13h)   

## ===사용법===
![image](https://user-images.githubusercontent.com/88232976/198500304-d2fee6f2-7032-48a5-b4ff-510373e6c55f.png)   
우리가 아스키코드로 변환하려는 코드는 3줄이니까 1줄씩 메모장에 복붙 하면 된다.   
![image](https://user-images.githubusercontent.com/88232976/198501032-8bc0fd41-6944-42f1-a500-db5f7c74a763.png)   
첫 번째 줄을 입력 했으면 __,(띄어쓰기) __ 를 눌러 형식에 맞춰줘야 한다.   
![image](https://user-images.githubusercontent.com/88232976/198501295-fbf60e8f-f86d-4f60-9040-da70293475b1.png)   
이렇게 다 했으면 이 코드를 복사해서 프로그램의 입력 값으로 넣으면 된다.

## ===실행===
![image](https://user-images.githubusercontent.com/88232976/198501413-d867ddb2-7695-4811-a8c9-1cb9e3d5f92f.png)   




## ===코드===
```
a=list(input().split(','))
for i in a:
    if(i[-1]=='h'):
        print(chr(int("0x"+i.strip('h| '),16)),end='')
    elif(i[-1]==')'):
        temp=list(i.split(' '))
        temp[0]=int(temp[1])
        temp[1]=int("0x"+temp[1].strip("dup|)|(|h| "),16)
        for i in range(temp[0]):
            print(chr(temp[1]),end='')
```
