# 适配器模式 ( Adapter )
  
## 别名

> Wrapper (包装器)

## 用途

> 将一个类的接口转换成客户希望的另外一个接口。 Adapter模式使得原本由于接口不兼容
  而不能一起工作的那些类可以一起工作。

## 实例

> 假设一下你的存储卡里有一些照片，你需要把它们转移到你的电脑上。为了转移它们，你
需要一些与你的电脑接口兼容的适配器，这样你就可以将存储卡连接到你的电脑上。这里，
读卡器就起到了适配器的作用。更经典的例子就是人尽皆知的电源适配器了，一个三脚的
插头不能连接到两个孔的插座上，它需要一个电源适配器，使它与两个分叉的插座兼容。

## 模式分析

> 假定现在有一个小汽车司机，他只会驾驶小型汽车，并不会驾驶公共汽车。
>
> 现在分别定义小汽车 ( Car ) 和公共汽车 ( Bus ) 两种接口

```
public interface Car {
  void drive();
}

public class Bus {
  private static final Logger LOGGER = LoggerFactory.getLogger(Bus.class);
  public void run() {
    LOGGER.info("公共汽车在行驶");
  }
}
```
> 这个司机需要获得一辆小汽车才能进行驾驶活动

```
public class Driver implements Car {
  private Car car;
  @Override
  public void drive() {
    car.drive();
  }
  public Driver(Car car) {
    this.car = car;
  }
}
```
## 适用场景