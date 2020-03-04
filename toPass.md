```c++
#include<iostream>
using namespace std;
int main() {
	int c, r, num;
	cin >> c >> r;
	cin >> num;
	if (c * r == num || num == 0) {
		cout << 0 << endl;
		return 0;
	}
	if (c * r == 1) {
		cout << 1 << endl;
		return 0;
	}
	int arr[51][51] = { 0 };

	int m, n;
	for (int d = 0; d < num; d++) {
		cin >> m >> n;
		arr[m+1][n+1] = -1;
	}
	for (int i = 1; i < c+1; i++) {
		for (int j = 1; j < r+1; j++) {
			if (arr[i][j] == -1) {
				for (int p = i - 1; p <= i + 1; p++) {
					for (int q = j - 1; j <= j + 1; q++) {
						if (p != i || q!= j)
							arr[p][q] ++;
					}
				}
			}


		}
	}
	int sum = 0;
	for (int x = 1; x < c+1; x++) {
		for (int y = 0; y < r+1; y++) {
			sum = sum + arr[x][y];
		}
	}
	cout << sum + num << endl;
	return 0;
}
