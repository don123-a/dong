通过交流群中分享的教程及在B站上查找初步掌握C语言，但对于代码不太熟悉，需要借助网络查找，完成作业主要通过文件中提供的数据，在vs上运行错误后询问AI代码了解运行方式再进行改正，第三题无法完成，但前两题注释很仔细，我需要更多的时间去学习

1.作业一：
#include <iostream>
using namespace std;

// 1. 计算第n个斐波那契数
long long fibonacci_nth(int n) {
    if (n == 0) return 0;
    if (n == 1) return 1;
    long long a = 0, b = 1, c;
    for (int i = 2; i <= n; i++) {
        c = a + b;
        a = b;
        b = c;
    }
    return b;
}

// 2. 输出前n项斐波那契数列（每行8个数字）
void fibonacci_sequence(int n) {
    cout << "前" << n << "项斐波那契数列：" << endl;
    for (int i = 0; i < n; i++) {
        cout << fibonacci_nth(i) << " ";
        if ((i + 1) % 8 == 0) cout << endl; // 每8个换行
    }
    if (n % 8 != 0) cout << endl; // 补充换行
}

// 3. 计算前n项斐波那契数列的和（利用性质：前n项和 = F(n+2) - 1）
long long fibonacci_sum(int n) {
    return fibonacci_nth(n + 2) - 1;
}

int main() {
    int n;
    cout << "请输入整数n（0≤n≤90）：";
    cin >> n;

    // 输出第n项
    cout << "第" << n << "项斐波那契数：" << fibonacci_nth(n) << endl;

    // 输出前n项序列
    fibonacci_sequence(n);

    // 输出前n项和
    cout << "前" << n << "项和：" << fibonacci_sum(n) << endl;

    return 0;
}
2.作业二：
#include <iostream>
#include <cstdlib>
#include <ctime>
using namespace std;

// 生成随机数组
void generateArray(int arr[], int n) {
    srand(time(0)); // 设置随机种子
    for (int i = 0; i < n; i++) {
        arr[i] = rand() % 100; // 生成0~99的随机数
    }
}

// 打印数组
void printArray(int arr[], int n) {
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;
}

// 冒泡排序
void bubbleSort(int arr[], int n) {
    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                // 交换arr[j]和arr[j+1]
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }
}

// 选择排序
void selectionSort(int arr[], int n) {
    for (int i = 0; i < n - 1; i++) {
        int minIndex = i;
        for (int j = i + 1; j < n; j++) {
            if (arr[j] < arr[minIndex]) {
                minIndex = j;
            }
        }
        // 交换arr[i]与arr[minIndex]
        int temp = arr[i];
        arr[i] = arr[minIndex];
        arr[minIndex] = temp;
    }
}

int main() {
    const int SIZE = 10;
    int arr[SIZE];
    int original[SIZE]; // 用于保存原始数组

    // 生成随机数组
    generateArray(arr, SIZE);

    // 保存原始数组
    for (int i = 0; i < SIZE; i++) {
        original[i] = arr[i];
    }

    // 输出原始数组
    cout << "原始数组： ";
    printArray(original, SIZE);

    // 冒泡排序
    bubbleSort(arr, SIZE);
    cout << "冒泡排序： ";
    printArray(arr, SIZE);

    // 恢复原始数组
    for (int i = 0; i < SIZE; i++) {
        arr[i] = original[i];
    }

    // 选择排序
    selectionSort(arr, SIZE);
    cout << "选择排序： ";
    printArray(arr, SIZE);

    return 0;
}
3.作业三：
