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

## 抽象超类型的概念是什么？
采用更抽象更稳定的上层类型，而不是依赖更底层的具体实现类型。这里的“超”是supertype的直译，即上层类型。

## 为什么“针对接口编程”就是针对“超类型编程”？
针对接口编程 就是为了写代码时，把变量声明为接口，而不是具体实现类，然后运行时由多态决定调用哪一个实现。接口本身就是一种上层类型，面向接口编程就是面向上层抽象类编程。

## 什么是组合 Composition？
组合口就是一个内部“拥有”另一个对象，就是HAS-A关系。
举例：WeaponBehavior Weapon；
表示Character “有一个”WeaponBehavior，而不是通过继承把武器行为写死在Character里面。

## 什么是委托Delegation？
委托就是一个对象不自己完成某个行为，而是把这个任务交给另一个对象完成。
举例：weapon.useWeapon（）;
Character自己不负责怎么攻击，而是把攻击行为委托给WeaponBehavior对象。

## 为什么多用组合，少用继承？
继承容易把行为固定在类层级中，而组合可以吧行为做成独立对象，在运行时自由替换。
例如Character通过持有WeaponBehavior，可以随时从SwordBehavior替换成BowAndArrowBehavior，而不需要修改Character的继承结构。

## 共享模式词汇的概念
大家都懂设计模式之后，模式的名字本身就变成了一种共同语言，比如这里的Strategy Pattern  
不需要大串的解释：先做一个接口，再做几个不同实现，主类里面持有这个接口，行为可以替换，运行时通过多态决定执行那个。