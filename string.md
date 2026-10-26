String
字符表示单个，每个字符用单引号括起来，比如'a'。字符串是一个可变长度的字符序列，可以包含多个字符，用双引号括起来，比如"hello"。

    1.引入头文件
    使用string类型必须包含头文件<string>，作为标准库的一部分，string也被定义在命名空间std中

    #include <string>
    using std::string;

    2.声明和初始化

    string s1; // 默认初始化，s1是一个空的字符串
    string s2 = "hello"; // 初始化一个值为hello的字符串
    string s3(5, 'a') // 连续5个字符a组成的串，即'aaaaa'

    3.字符串操作

    使用 + 对字符串进行拼接操作，返回字符串连接之后的结果

    string s1 = "hello";
    string s2 = "world";
    string s3 = s1 + " " + s2; // 对字符串进行连接，拼接之后的字符串是"hello world", 中间加了空格

    使用 size() 来获取字符串长度

    int length = s1.size(); // 字符串的长度即字符串中字符的个数，"hello"的长度为5

    使用下标操作符 [] 来访问字符串中的每一位字符

    char c1 = s1[1]; // 下标从0开始，表示字符串的第一个字符

    使用 empty() 来判断字符串是否为空

    if (s1.empty()) {
    // 如果字符串为空则返回true, 否则返回false
    }

    4.输入输出string

    可以使用标准库中的 iostream 来读写string

    int main() {
    string s; // 定义空字符串
    // 将标准输入的内容读入到字符串s中，从第一个真正的字符（去掉空格、换行等）开始读取，直到遇到空白停止
    cin >> s; 
    cout << s << endl; // 输出s
    return 0;
    }

    仿照整数的读取流程，实现对文本的读取，并将读取的文本以空格隔开逐行输出到屏幕

    int main() {
    string word;
    while(cin >> word) { // 反复读取，直到到达末尾
        cout << word << endl; // 读取一个字符串并将其存储在 word 变量，然后输出，会附加一个换行符
    }
    }

    因为字符串读取遇到空格就会停止，表示这是一个单词，但有的时候我们需要读取一整句，这就要求我们的读取不能在空格处停止，这种情况下需要使用 getline() ，它会一直读取字符，直到遇到换行符（Enter键）或文件结束符（当读取文件内容时）结束。

    #include <iostream>
    #include <string>
    using namespace std;
    int main() {
    string line;
    // 获取用户输入的一行文本,并将其存储到line变量中
    getline(cin, line);
    // 输出读取的一行文本
    cout << line << endl;
    }