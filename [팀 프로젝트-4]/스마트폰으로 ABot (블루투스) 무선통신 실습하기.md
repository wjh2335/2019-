## 1. 유튜브 링크

## 2. 실습에 대한 자세한 설명(카페 참고, 개별)

>### ●아두이노 코드
```C
	#include <Servo.h>
	Servo sr, sl;
	void setup()
	{
		Serial.begin(9600);
		sr.attach(13);
		sl.attach(12);
	}
	void loop()
	{
		if (Serial.available())
		{
			  char b[2];
			  int p,r;
			  Serial.readBytes(b, 2);
			  p=b[0]*3;
			  r=b[1];
			  sr.write(1500+p-r);
			  sl.write(1500-p-r);
			  Serial.write('1');
		}
	}
```
>### ●앱인벤터

## 3. 소감
