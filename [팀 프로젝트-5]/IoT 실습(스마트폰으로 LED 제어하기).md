* # 유튜브 링크

[유튜브 링크](https://youtu.be/m8mJrXvAcB0)

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

```

이번 팀과제는 새로운 것을 배우는 게 아닌 배웠던 것들을 복습하는 것이라고 생각합니다.
전에 했던 것들을 기반으로 과제를 진행해서 수월하게 과제를 마치게 되었고 잊고 있던
것들을 상기시켜주는 과제였습니다. 교수님 덕분에 휴대폰으로 다른 장치를 작동시키는 것에
더욱 흥미가 붙고 있습니다. 더 열심히 노력해서 사람들 모두가 사용하는 휴대폰으로 다른
기기를 조작하는 앱과 실생활에 유용한 아두이노 장치를 만들겠습니다.
	
```
