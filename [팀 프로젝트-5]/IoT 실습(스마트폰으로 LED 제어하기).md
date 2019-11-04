* # 유튜브 링크
[유튜브 링크](https://youtube.com)
* # 소스코드
### 1. 아두이노 코드
```c
void setup()
{
  Serial.begin(9600);
  pinMode(13,OUTPUT);
}
void loop()
{
  if(Serial.available())
  {
    String m=Serial.readString();
    if(m.indexOf('0')==0) digitalWrite(13,LOW);
    if(m.indexOf('1')==0) digitalWrite(13,HIGH);
  }
}
```
### 2. 프로세싱 코드
```java
import processing.serial.*;
import processing.net.*;
Serial p;
Client c;
Server s;
void setup()
{
	p=new Serial(this,"COM3", 9600);
	s=new Server(this,12345);
	textSize(64);
}
void draw()
{
	c=s.available();
	if(c!=null)
	{
		String m=c.readString();
		m=m.substring(m.length()-1);
		print(m);
		p.write(m);
	}
}
```
* # 앱인벤터

>![1](/img/7.png)
>
>	**▲앱 모습**
>
>![1](/img/8.PNG)
>
>	**▲구성 요소**
>
>![1](/img/9.png)
>
>	**▲블럭**

* # 소감
	ㄴㅇㄹ
