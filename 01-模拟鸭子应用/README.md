## 这里一直提到的OO，Object-Oriented是什么概念？
object是在class创建出的一个具体实例，而每个object又拥有自己的数据，那么object-oriented是表达以object为核心，思考object负责什么，由谁处理，怎么合作。
举个例子：Duck, performFly, fly以及FlyBehavior之间的关系
```java
interface FlyBehavior{
    void fly();
}

class FlyWithWings implements FlyBehavior{  
    public void fly(){
        System.out.println("I fly with wings");
    }
}

class Duck{
    FlyBehavior flyBehavior;

    void performFly(){
        flyBehavior.fly();
    }
}

class greenDuck extends Duck{
    GreenDuck(){
        flyBehavior = new FlyWithWings();
    }
}

```
Duck在此处不负责具体怎么飞，FlyWithWings负责具体飞行方式，Duck和FlyWithWings合作完成飞行，performFly的行为由Duck提供
