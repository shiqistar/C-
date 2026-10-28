在刷题过程中 面向对象 使用的比较少，但是工程化开发中。面向对象却是很重要的内容，本节课我们借助一道题目学习 C++ 中面向对象的一些知识，你也可以使用简易的方法轻松的解决本道题目，但是我们更希望你对类和面向对象中的三大特性：封装、继承、多态有更多的了解。
1. 类 和面向对象

C++ 是一种多范式编程语言，支持过程编程和面向对象编程，它将数据和操作数据的方法组织为类和对象。

我们可以将之抽象为一个类Person, 并具有一些“属性”和“方法”。

    “属性”表示Person类所具有的特征，比如姓名、年龄、性别，通过这些特征，我们可以描述一个“人”的基本状态。
    “方法”表示Person类的行为和功能，比如吃饭、睡觉、行走，通过这些动作，我们可以描述一个“人”的动态行为。

比如下面的“伪代码”表示Person类的定义, 它包括姓名、性别、年龄和吃饭的方法。

    Person {
        // 姓名、性别、年龄等属性
        name;
        gender;
        age;
          // 吃饭的方法
          eat() {
        }
        // 行走的方法
        walk() {
        
        }
    }

这样在计算机世界，一个“人”的概念就建立起来了，但这里的Person类只是个“模具”，空有概念，而无法表示具体的某一个人，只有创造一个类的实例（也就是我们说的对象），比如"张三，18， 男", "李明、20，男"，才能真正的使用。

现在你是不是能对面向对象有一些初步的理解了呢？

简而言之，“类”是现实世界中的实体在计算机世界中的抽象概念，类可以看作是对象的模板，它定义了对象的结构和行为方式，可以用来创建具有相同属性和行为的多个对象，而对象是“类”的实现。

了解了概念之后，我们先了解一下类的基本写法：

    class 类名{
    访问修饰符:
              // 成员变量，表示类的属性， 定义方式和变量的定义一样
          // 成员方法，表示类的行为， 定义方式和方法的定义一样
    }; // 分号结束一个类

2.封装

封装是面向对象的三大特性之一，封装的主要目的是为了保证数据的安全性，我们假设有一个Circle类，它具有半径这个属性。

    class Circle {
    public:
        // 成员变量
        int radius;
    };

然后我们创建一个圆对象

    Circle circe; // 创建一个对象

创建对象之后，外部代码可以直接访问和修改半径，甚至将其设置为负数，这样的设计显然是不合理的。

    // 外部代码没有经过验证可以直接访问和修改半径
    circle.radius = 10

为了防止这些问题的发生，我们可以通过封装隐藏对象中一些不希望被外部所访问到的属性或方法，具体怎么做呢？可以分为两步：

    将对象的属性名，设置为private，只能被类所访问
    提供公共的get和set方法来获取和设置对象的属性

    class Circle {
    // 私有属性和方法
    private:
        int radius;  // 将圆的半径设置为私有的
    // 公有属性和方法
    public:
          // setXX方法设置属性
        void setRadius(int r) {
              radius = r;
        }
            // getXXX方法获取属性
        int getRadius() {
            return radius;
        }
    };

使用封装，我们隐藏了类的一些属性，具体的做法是使用get方法获取属性，使用set方法设置属性，如果希望属性是只读的，则可以直接去掉set方法，如果希望属性不能被外部访问，则可以直接去掉get方法。此外我们还可以在读取属性和修改属性的同时做一些其他的处理，比如如下的操作：

    void setRadius(int r) {
          // 对输入的半径进行验证，只有半径大于0，才进行处理
        if (r >= 0) {
            radius = r;
        } else {
            cout << "半径不能为负数" << endl;
        }
    }

3.构造函数

在学习继承之前，我们先来复习一下构造函数的知识，类的构造函数和之前结构体的构造函数类似，用于初始化对象的成员变量，构造函数与类同名，没有返回类型，并且在对象创建时自动调用。其基本语法包括：

    函数名：与类名相同
    参数列表：可以有零个或多个参数，用于在创建对象时传递初始化信息。
    函数体： 用于执行构造函数的初始化逻辑。

下面我们还以Person类作为示例，包含一个默认构造函数和带参数的构造函数。

    const string& personName表示对string类型对常量引用，你可以传递字符串参数，但是不能在函数中修改这个参数的值。

    class Person {
    private:
      int age;
      string name;
    public:
      // 默认构造函数
      Person() {
        age = 20;
        name = "Tom"
      }
      // 带参数的构造函数
      Person(int personAge, const string& personName) {
        age = personAge;
        name = personName
      }
    }
    int main() {
        // 使用默认构造函数创建对象
        Person person1;
     
        // 使用带参数的构造函数创建对象
        Person person2(20, "Jerry");
      
        return 0;
    }

此外，还有构造函数的成员初始化列表写法，这种写法允许在进入构造函数主体之前对类成员进行初始化，比如下面的示例。

    Person(int personAge, const string& personName) : age(personAge), name(personName) {
        
    }

在上面的代码中， Person 类的构造函数接受一个 string 类型的参数 persnName和一个int类型的参数personAge，并通过成员初始化列表初始化了 成员变量。在这里，: age(personAge), name(personName) 表示将 personAge 的值赋给 age 成员变量, 将 personName 的值赋给 name , 从而完成了成员变量初始化。
4.继承

在对象中，总有一些操作是 重复的 ，比如说Person类具有姓名、身高、年龄等特征，并具有一些行走、吃饭、睡觉的方法，而我们要实现一个Teacher类，Teacher首先也是一个人，他也具备人的特征和方法，那我们是不是也应该用代码去实现这些特征和方法呢，这就势必会产生一些重复的代码。

因此，我们可以采用“继承”的方式使得一个类获取到其他类中的属性和方法。在定义类时，可以在类名后指定当前类的父类（超类), 子类可以直接继承父类中的所有属性和方法，从而避免编写重复性的代码，此外我们还可以对子类进行扩展。

假设，我们有一个图形类Shape, 它具有一个属性和一个方法，属性为类型，方法为求图形的面积

    class Shape {
    protected:
        string type;  // 形状类型
     
    public:
        // 构造函数
        Shape(const string& shapeType) : type(shapeType) {}
     
        // 求面积的函数
        double getArea() const {
            return 0.0;
        }
     
        // 获取形状类型
        string getType() const {
            return type;
        }
    };

在上面的代码中，getArea函数使用const用来修饰，是用来表示该函数不会修改对象的状态，使用const能保证对对象的访问是安全的。

    double getArea() const {
          // 不会修改对象的状态
          return 0.0;
    }

要想实现继承，我们还需要一个关于圆的类Circle，它继承自Shape类

    // Circle 类，继承自 Shape
    class Circle : public Shape {
    private:
        int radius;  // 圆的半径
     
    public:
        // 构造函数, 调用Shape的构造函数，初始化了类型为"circle"
        Circle(int circleRadius) : Shape("Circle"), radius(circleRadius) {}
     
        // 重写基类的方法
        double calculateArea() const override{
            return 3.14 * radius * radius;  // 圆的面积公式
        }
     
        // 获取半径
        int getRadius() const {
            return radius;
        }
    };

在上面的示例代码中，图形类拥有shape属性和getArea、getType方法，而子类在父类这些属性和方法的基础上新增了radius属性和getRadius方法，并且在子类和父类中都有getArea这个方法，这被称为方法的重写，方法的重写需要override关键字，其意思是子类重写父类的方法，并提供自己的实现。
5.多态

多态常常和继承紧密相连，它允许不同的对象使用相同的接口进行操作，但在运行时表现出不同的行为。多态性使得可以使用基类类型的指针或引用来引用派生类的对象，从而在运行时选择调用相应的派生类方法。

C++中实现多态性的方法是通过virtual虚函数，比如下面的示例：

    class Shape {
    public:
        virtual double calculateArea() const = 0;
    };
    class Circle : public Shape {
    private:
        int radius;
     
    public:
        double calculateArea() const override {
            return 3.14 * radius * radius;
        }
    };
    class Rectangle : public Shape {
    private:
        int width;
        int height;
     
    public:
        // 构造函数，用于初始化 width 和 height
        Rectangle(int w, int h) : width(w), height(h) {}
        // width * height 的结果是整数，但 calculateArea 方法的返回类型是 double
        // 为了确保结果是一个浮点数，使用 static_cast<double> 将其显式转换为 double 类型
           double calculateArea() const override {
            return static_cast<double>(width * height);
        }
    };

这里使用virtual在父类中定义了一个虚函数，而= 0表示这是一个纯虚函数，即定义的函数在基类中没有实现，但是要求它的派生类都必须提供这个函数的实现，这种抽象的方法使得 Shape 类成为一个抽象基类，不能被实例化，只能被用作派生其他类的基类。

然后两个派生类 Circle 和 Rectangle则是重写了 calculateArea 方法，它们提供了各自的实现，有着不同的计算逻辑。

    int main() {
        std::vector<Shape*> shapes;
     
        shapes.push_back(new Rectangle(4, 5));
        shapes.push_back(new Circle(3));
     
        for (const Shape* shape : shapes) {
            std::cout << "Area: " << shape->calculateArea() << std::endl;
        }
     
        return 0;
    }

之后我们创建了一个容器shapes，包含不同类型的图形对象，然后循环遍历该容器并为每一个shape对象调用 calculateArea 方法，尽管方法名称相同，但实际调用的方法是根据对象的类型动态确定的，这其实就是多态的概念。