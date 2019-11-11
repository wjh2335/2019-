# 1. 회로 만들기
## 1.1. 회로도
![1](/img/10.jpg)

#### ▲ 회로도
![1](/img/11.jpg)

#### ▲ 실제로 만든 회로
```
회로도에 나와있는 2KΩ 저항을 사용하니 인식범위가 넓어 1KΩ 저항을 사용했습니다.
```
## 1.2. 저항
* #### 저항은 색 3개를 이용해서 그 저항이 몇 Ω인지 나타냅니다.
* #### 처음 2개 색은 저항의 값이고, 마지막 색은 곱해야 하는 값입니.
* #### 저항의 값은 다음 표와 같습니다.
|색|값|곱|
|:-:|:-:|:-:|
| 🖤 |0|1|
| 🤎 |1|10|
| ❤ |2|100|
| 🧡 |3|1000|
| 💛 |4|10000|
| 💚 |5|100000|
| 💙 |6|1000000|
| 💜 |7|10000000|
| Grey |8|100000000|
| White |9|1000000000|
# 2. 기본적인 테스트

* #### 적외선 센서를 테스트 하는 코드입니다.
* #### 적외선 감지 여부에 따라 1또는 0을 출력합니다.

```c
void setup()
{
	pinMode(10,INPUT);
	pinMode(9,OUTPUT);
	pinMode(3,INPUT);
	pinMode(2,OUTPUT);
	Serial.begin(9600);
}
int irDetect(int irLedPin,int irReceiverPin,long frequency)
{
	tone(irLedPin, frequency, 8);
	delay(1);
	int ir=digitalRead(irReceiverPin);
	delay(1);
	return ir;
}
void loop()
{
	int irLeft=irDetect(9, 10, 38000);
	Serial.print(irLeft);
	int irRight=irDetect(2, 3, 38000);
	Serial.print("  ");
	Serial.println(irRight);
	delay(100);
}
```
# 3. 영혼을 불어 넣기
* #### 아두이노 로봇이 장애물을 판단하고 방향전환을 할 수 있도록 코드를 짜 업로드를 해줍니다.
```c
#include <Servo.h>

Servo servoLeft;
Servo servoRight;

void setup()
{
	pinMode(10,INPUT);
	pinMode(9,OUTPUT);
	
	pinMode(3,INPUT);
	pinMode(2,OUTPUT);
	
	servoLeft.attach(13);
	servoRight.attach(12);
}
void loop()
{
	int irLeft=irDetect(9,10,38000);
	int irRight=irDetect(2,3,38000);
	if(irLeft==0 && irRight==0)
	{
		backward(1000);
		turnLeft(800);
	}
	else if(irLeft==0)
	{
		backward(1000);
		turnRight(400);
	}
	else if(irRight==0)
	{
		backward(1000);
		turnLeft(400);
	}
	else forward(20);
}
int irDetect(int irLedPin,int irReceiverPin,long frequency)
{
	tone(irLedPin,frequency,8);
	delay(1);
	int ir=digitalRead(irReceiverPin);
	delay(1);
	return ir;
}
void forward(int time)
{
	servoLeft.write(1700);
	servoRight.write(1300);
	delay(time);
}
void turnLeft(int time)
{
	servoLeft.write(1300);
	servoRight.write(1300);
	delay(time);
}
void turnRight(int time)
{
	servoLeft.write(1700);
	servoRight.write(1700);
	delay(time);
}
void backward(int time)
{
	servoLeft.write(1300);
	servoRight.write(1700);
	delay(time);
}
```
# 4. 유튜브 링크
[유튜브 링크](https://youtu.be/Jhb8Jn83JBw)

# 5. 소감
```
오늘 창의공학 강의 내용인 수신기를 이용하여 로봇 자율 주행에 대해 팀 끼리 함께 토론을 하며 실습했습니다.
다른 친구들과 함께 다양한 의견을 주고받는 것을 혼자서 실험해보며 공부하는 것 보다 더 많은 생각을 할 수 
있었습니다. 팀원들 각각이 가지고 있던 닫힌 사고에서 벗어나, 다른 팀원들의 참신한 의견들이 모여서 이번 실습에서
있었던 많은 문제들을 해결할 수 있었다고 생각합니다. 처음 시도했을 때 Abot이 자꾸만 뒤로 이동하고, 인식하는
범위가 너무 넓은 문제가 있었습니다. 문제를 해결하기 위해 서보모터 핀을 바꾸어 소스코드를 수정하였고, 저항의
종류를 바꾸었습니다. 이러한 과정을 통하여 문제를 해결하였습니다. 교수님이 아두이노 카페에 올려주신 참고자료가
많은 도움이 되었습니다. 감사합니다.
```
