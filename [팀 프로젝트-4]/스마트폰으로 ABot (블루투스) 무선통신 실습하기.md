# 1. 유튜브 링크
[유튜브 링크](https://youtu.be/b2sexwxmPP8)
# 2. 실습에 대한 자세한 설명(카페 참고, 개별)

* ## 아두이노 코드
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
* ## 앱인벤터

>![1](/img/4.png)
>
>	**▲앱 모습**
>
>![1](/img/5.png)
>
>	**▲구성 요소**
>
>![1](/img/6.png)
>
>	**▲블럭**

## 3. 소감

	블루투스를 이용해서 스마트폰의 기울기에 따라 아두이노 봇이 움직이는게 신기했습니다.
	소스코드와 앱인벤터의 자료를 공부함으로써 스마트폰의 블루투스 신호가 어떤 과정을 통해
	아두이노에 도달하는지, 피치와 롤 값을 받아서 1500±p-r와 같이 사용하는 방법도 알게
	되었습니다. 아두이노 사랑합니다~♡
