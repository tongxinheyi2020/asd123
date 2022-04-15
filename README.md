## v2ray-heroku
[![](https://www.herokucdn.com/deploy/button.png)](https://heroku.com/deploy?template=https://github.com/tongxinheyi2020/asd123.git)

### heroku�ϲ���v2ray
- [x] ֧��VMess��VLESS����Э��
- [x] ֧���Զ���websocket·��
- [x] αװ��ҳ��3DԪ�����ڱ�
- [x] HTML5����
- [x] ʹ��v2ray���°湹��

����`/`������3DԪ�����ڱ�

![image](https://cdn.jsdelivr.net/gh/DaoChen6/Heroku-v2ray/doc/1.png)

����`/speedtest/`��html5-speedtest����ҳ��

![image](https://cdn.jsdelivr.net/gh/DaoChen6/Heroku-v2ray/doc/2.png)

����`/test/`���ļ������ٶȲ���

![image](https://cdn.jsdelivr.net/gh/DaoChen6/Heroku-v2ray/doc/3.png)

����`/ray`�������ã�v2ray websocket·��


### ��������˵��

|  ���� | ֵ  | ˵��  |
| ------------ | ------------ | ------------ |
|  PROTOCOL |  vmess<br>vless����ѡ�� |  Э�飺nginx+vmess+ws+tls����nginx+vless+ws+tls |
|  UUID |  [uuid����������](https://www.uuidgenerator.net "uuid����������") | �û���ID  |
|  WS_PATH | Ĭ��Ϊ`/ray` |  ·��������ʹ��`/speedtest`��`/`��`/test` ���Ѿ���ռ�õ�����·�� |

### ����
heorku���԰󿨣�Ӧ��һֱ���ߣ����۷ѣ�������������cf��[uptimerobot](https://uptimerobot.com/) ��ʱ���ʷ�ֹ���ߣ�ֻ���CF Workers������ַ���ˣ���Ȼ�����˻�һ����û����Ͱ�ʱ������ˣ�

### CloudFlare Workers�������루�ɷֱ��������˺ŵ�Ӧ�ó�������`PROTOCOL`��`UUID`��`WS_PATH`����һ�£�����˫����ֱ�ִ�У���һ���¾���550+550Сʱ��
<details>
<summary>CloudFlare Workers���˻���������</summary>

```js
addEventListener(
    "fetch",event => {
        let url=new URL(event.request.url);
        url.hostname="appname.herokuapp.com";
        let request=new Request(url,event.request);
        event. respondWith(
            fetch(request)
        )
    }
)
```
</details>

<details>
<summary>CloudFlare Workers��˫���ֻ���������</summary>

```js
const SingleDay = 'app0.herokuapp.com'
const DoubleDay = 'app1.herokuapp.com'
addEventListener(
    "fetch",event => {
    
        let nd = new Date();
        if (nd.getDate()%2) {
            host = SingleDay
        } else {
            host = DoubleDay
        }
        
        let url=new URL(event.request.url);
        url.hostname=host;
        let request=new Request(url,event.request);
        event. respondWith(
            fetch(request)
        )
    }
)
```
</details>

<details>
<summary>CloudFlare Workersÿ�����ֻ�һ��ʽ��������</summary>

```js
const Day0 = 'app0.herokuapp.com'
const Day1 = 'app1.herokuapp.com'
const Day2 = 'app2.herokuapp.com'
const Day3 = 'app3.herokuapp.com'
const Day4 = 'app4.herokuapp.com'
addEventListener(
    "fetch",event => {
    
        let nd = new Date();
        let day = nd.getDate() % 5;
        if (day === 0) {
            host = Day0
        } else if (day === 1) {
            host = Day1
        } else if (day === 2) {
            host = Day2
        } else if (day === 3){
            host = Day3
        } else if (day === 4){
            host = Day4
        } else {
            host = Day1
        }
        
        let url=new URL(event.request.url);
        url.hostname=host;
        let request=new Request(url,event.request);
        event. respondWith(
            fetch(request)
        )
    }
)
```
</details>

<details>
<summary>CloudFlare Workersһ���ֻ���������</summary>

```js
const Day0 = 'app0.herokuapp.com'
const Day1 = 'app1.herokuapp.com'
const Day2 = 'app2.herokuapp.com'
const Day3 = 'app3.herokuapp.com'
const Day4 = 'app4.herokuapp.com'
const Day5 = 'app5.herokuapp.com'
const Day6 = 'app6.herokuapp.com'
addEventListener(
    "fetch",event => {
    
        let nd = new Date();
        let day = nd.getDay();
        if (day === 0) {
            host = Day0
        } else if (day === 1) {
            host = Day1
        } else if (day === 2) {
            host = Day2
        } else if (day === 3){
            host = Day3
        } else if (day === 4) {
            host = Day4
        } else if (day === 5) {
            host = Day5
        } else if (day === 6) {
            host = Day6
        } else {
            host = Day1
        }
        
        let url=new URL(event.request.url);
        url.hostname=host;
        let request=new Request(url,event.request);
        event. respondWith(
            fetch(request)
        )
    }
)
```
</details>
