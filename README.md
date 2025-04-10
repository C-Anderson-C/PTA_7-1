# PTA_7-1
# 厘米换算英尺英寸
# 题目：如果已知英制长度的英尺foot和英寸inch的值，那么对应的米是(foot+inch/12)×0.3048。现在，如果用户输入的是厘米数，那么对应英制长度的英尺和英寸是多少呢？别忘了1英尺等于12英寸。
# 输入格式：输入在一行中给出1个正整数，单位是厘米。
# 输出格式：在一行中输出这个厘米数对应英制长度的英尺和英寸的整数值，中间用空格分开。英寸的值应小于12。
```cpp
#include<iostream>
#include<cmath>
using namespace std;

int main() {
    int cm;
    cin >> cm;
    if (cm == 0) { //如果输入为0厘米，则输出位0英尺 0英寸
        cout << "0" << " " << "0" << endl;
        return 0;
    }
    else {
        int foot = static_cast<int>(cm / 30.48);  //截断小数只要整数部分，将double类型转换为int类型
        double inch = (cm - foot * 30.48) / 2.54; //先算出inch部分
        int inch_non = static_cast<int>(inch);  //截断inch部分，转为int类型
        if (inch_non >= 12) {  //inch不得超过12，将超过12的部分转换为foot
            foot += inch_non / 12;
            inch_non = inch_non % 12;
        }
        cout << foot << " " << inch_non << endl;  //按照题目条件输出结果
        return 0;
    }
}