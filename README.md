
#include <iostream>
using namespace std;

// 1. 计算第n个斐波那契数（迭代法避免递归栈溢出）
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
