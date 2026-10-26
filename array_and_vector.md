数组：

C++中声明数组的方式为dataType arrayName[arraySize]。

    dataType表示数组元素的类型，比如int、double、char等。
    arrayName是为数组指定的名称，类似于变量名称。
    arraySize是数组的大小，即它可以容纳多少个元素

    // 声明一个包含5个整数的数组
    int myArray[5];

    // 使用大括号初始化一个长度为5的整型数组
    int arr[5] = {1, 2, 3, 4, 5}; 
    
    // 定义一个长度为3的整型数组，并逐个赋值
    int arr1[3];
    arr1[0] = 10;
    arr1[1] = 20;
    arr1[2] = 30; 

    int value = arr[2]; // 获取数组 arr 的第三个元素的值，即 3

    arr[0] = 100;  // 修改数组 arr 的第一个元素的值为 100

    for (int i = 0; i < 5; i++) {
        cout << arr[i] << " ";
    } // 遍历数组

    int a = arr[5]; // 数组长度为5，索引范围为0-4，如果尝试访问arr[5]，会越界访问数组范围，导致程序运行出错

容器：

如果不确定元素的具体个数，可以使用vector。
vector，也称容器，做为C++标准库中的一个容器类，表示对象的集合，它可以动态地存储一组元素，所以可以根据需要调整vector的大小。
和输入输出类似，使用vector，必须包含头文件vector
    #include <vector>
    sing std::vector;

    vector<int> myVector; // 创建一个空vector, 元素是int类型的

    vector<int> myVector = {1, 2, 3, 4, 5}; // 创建一个包含整数元素的容器并初始化元素
 
    vector<int> myVector(10); // 创建一个包含10个元素的容器，元素为int类型（值被系统默认初始化为0）
 
    vector<int> myVector(10, -1); // 创建一个包含10个重复元素的容器，每个元素的值都是-1

    vector可以动态调整大小，通过vector内置的方法push_back动态添加元素来实现
    push_back() 负责将一个值 push(推送) 到vector中的back(尾端)
    vector<int> myVector = {1, 2, 3, 4, 5};
    myVector.push_back(6); // 往容器的最末端添加数字6

    int value = myVector[0]; // 获取第一个元素的值，即 1

    int size = myVector.size(); // 获取vector的大小

    for (int i = 0; i < myVector.size(); i++) {
        cout << myVector[i] << " "; // 从索引为0开始，遍历到i等于size的时候退出循环，完成整个遍历
    }

    myVector.pop_back(); // 删除vector末尾的元素
    myVector.clear(); // 清空vector中的所有元素
    myVector.empty(); // 判断vector是否不含有任何元素，如果长度为0，则返回真，否则，返回假