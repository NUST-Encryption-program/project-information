#依赖注入
=================================================================

***


依赖注入不是目的，它是一系列工具和手段，最终的目的是帮助我们开发出松散耦合(loose coupled)、可维护、可测试的代码和程序。这条原则的做法是大家熟知的面向接口，或者说是面向抽象编程。

什么是依赖注入？

Stack Overflow的经典解释：“When you go and get things out of the refrigerator for yourself, you can cause problems. You might leave the door open, you might get something Mommy or Daddy doesn’t want you to have. You might even be looking for something we don’t even have or which has expired.

What you should be doing is stating a need, “I need something to drink with lunch,” and then we will make sure you have something when you sit down to eat.”

###示例

**1）一般情况下的类耦合**

```
Main.java

public class Main {
     public static void main(String[] args) {
          /******** 一般写法，Main类与Chinese类和American类之间的强耦合 ***********/
          // Chinese和American，当类和方法修改时，此处的类和方法也需要修改
          Chinese chinese = new Chinese();
          chinese.sayHelloWorld("张三");

          American american = new American();
          american.sayHelloWorld("Jack");
     }
}

/******************** 一般方法 ***************************/

interface Human {
     public void sayHelloWorld(String name);
}


class Chinese implements Human {
     public void sayHelloWorld(String name) {
          String helloWorld = "你好，" + name;
          System.out.println(helloWorld);
     }
}

class American implements Human {
     public void sayHelloWorld(String name) {
          String helloWorld = "Hello，" + name;
          System.out.println(helloWorld);
     }
}
```

通过上面代码可以看出：Main类与Chinese类和American类之间存在着强耦合 ， Chinese和American类和方法修改时，此处的类和方法也需要修改。不容易扩展和维护。

 

**2）工厂方法来解耦合**


```
public class Main {
     public static void main(String[] args) {
          /******** 工厂方法， Main类与类Chinese和American不再耦合，仅仅和其接口Human耦合 ***********/
          // 修改时还需要修改在Main类中修改这些字符串
          // Chinese和American，当类和方法修改时，只有方法需要修改
          HumanFactory humanFactory = new HumanFactory();
          Human human1 = humanFactory.getHuman("chinese");
          human1.sayHelloWorld("张三");

          Human human2 = humanFactory.getHuman("american");
          human2.sayHelloWorld("Jack");
     }
}


/******************** 工厂方法 ***************************/
interface Human {
     public void sayHelloWorld(String name);
}

class HumanFactory {
     public Human getHuman(String type) {
          if ("chinese".equals(type)) {
               return new Chinese();
          } else {
               return new American();
          }
     }
}
```

通过上面代码可以看出：Main类与类Chinese和American不再耦合，仅仅和其接口Human耦合，修改时还需要修改在Main类中修改这些字符串，当类和方法修改时，只有方法需要修改。这一定程度上降低了Main类和Chinese、American类的耦合

**3）依赖注入和控制反转**

```
public class Main {
     public static void main(String[] args) {
          /******************** IOC控制反转和依赖注入 ***************************/
          // 利用容器，通过xml文件直接注入属性值，在Main类中只添加需要的
          // Chinese和American，当类和方法修改时，代码完全不用修改，只需要修改xml文件即可，彻底实现了解耦
          BeanFactory beanFactory = new BeanFactory();
          beanFactory.init("/config.xml");
          UserBean userBean = (UserBean) beanFactory.getBean("userBean");
          System.out.println("userName=" + userBean.getUserName());
          System.out.println("password=" + userBean.getPassword());
     }
}


/******************** IOC控制反转和依赖注入 ***************************/
// 下面是Spring的IOC实现：Bean工厂
class BeanFactory {
     private Map<String, Object> beanMap = new HashMap<String, Object>();

     public void init(String fileName) {
          try {
               // 读取指定的配置文件
               SAXReader reader = new SAXReader();
               // System.out.println(xmlpath);
               String realPathString = new File("").getCanonicalPath();
               Document document = reader.read(new File(realPathString + "/src/com/devin/") + fileName);
               Element root = document.getRootElement();
               Element foo;
               // 遍历bean
               for (Iterator i = root.elementIterator("bean"); i.hasNext();) {
                    foo = (Element) i.next();
                    // 获取bean的属性id和class
                    Attribute id = foo.attribute("id");
                    Attribute cls = foo.attribute("class");
                    // 利用Java反射机制，通过class的名称获取Class对象
                    Class bean = Class.forName(cls.getText());
                    // 获取对应class的信息
                    java.beans.BeanInfo info = java.beans.Introspector.getBeanInfo(bean);
                    // 获取其属性描述
                    java.beans.PropertyDescriptor pd[] = info.getPropertyDescriptors();
                    // 设置值的方法
                    Method mSet = null;
                    // 创建一个对象
                    Object obj = bean.newInstance();
                    // 遍历该bean的property属性
                    for (Iterator ite = foo.elementIterator("property"); ite.hasNext();) {
                         Element foo2 = (Element) ite.next();
                         // 获取该property的name属性
                         Attribute name = foo2.attribute("name");
                         String value = null;
                         // 获取该property的子元素value的值
                         for (Iterator ite1 = foo2.elementIterator("value"); ite1.hasNext();) {
                              Element node = (Element) ite1.next();
                              value = node.getText();
                              break;
                         }
                         for (int k = 0; k < pd.length; k++) {
                              if (pd[k].getName().equalsIgnoreCase(name.getText())) {
                                   mSet = pd[k].getWriteMethod();
                                   mSet.invoke(obj, value);
                              }
                         }
                    }

                    // 将对象放入beanMap中，其中key为id值，value为对象
                    beanMap.put(id.getText(), obj);
               }
          } catch (Exception e) {
               System.out.println(e.toString());
          }
     }

     // 通过bean的id获取bean的对象.
     public Object getBean(String beanName) {
          Object obj = beanMap.get(beanName);
          return obj;
     }
}


UserBean.java

public class UserBean {
     private String userName;
     private String password;

     public String getPassword() {
          return password;
     }

     public String getUserName() {
          return userName;
     }

     public void setUserName(String userName) {
          this.userName = userName;
     }

     public void setPassword(String password) {
          this.password = password;
     }
}

config.xml

<?xml version="1.0" encoding="UTF-8"?>
<beans>
     <bean id="userBean" class="com.devin.UserBean">
          <property name="userName">
               <value>张三</value>
          </property>
          <property name="password">
               <value>Jack</value>
          </property>
     </bean>
</beans>
```

说明：模拟了Spring中IOC的实现，虽然只是完成了Spring中依赖注入的一小部分工作，但是很好的展现了Java反射机制在Spring中的应用，能使我们能更好的从原理上了解IOC的实现。
