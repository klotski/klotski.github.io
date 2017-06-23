---
layout: default
title: Classic Problems in Programming
category: Programming
---

[TOC]

---

### 平均值
Notes:
1. 平均值应该定义为 double 型
2. 避免整型相除，如 `int c = (a+b)/2` 应该是 `double c = (a+b)/2.0`
```c
#include <stdio.h>

int main(int argc, char const *argv[])
{
	int sum = 0;
	int count = 0;
	int number;

	scanf("%d", &number);
	while ( number != -1 ) {
		sum += number;
		count ++;
		scanf("%d", &number);
	}

	double dsum = sum;
	printf("The average is %f.\n", dsum / count);

	return 0;
}
```

### 时区转换
```c
#include <stdio.h>

int main(int argc, char const *argv[])
{
	int utc, bjt, hour, minute;
	
	printf ("Enter UTC time: ");
	scanf ("%d", &utc);
	hour = utc / 100;
	minute = utc % 100;
	
	if (hour < 8) {
		hour = hour - 8 + 24;
	} else {
		hour = hour - 8;
	}
	
	bjt = hour * 100 + minute;
	printf ("BJT time is %d\n", bjt);
		
    return 0;
}
```

### 鸡兔同笼
```c
#include <stdio.h>

int main(int argc, char const *argv[])
{
	int heads = 0,  feet = 0;
	printf ("请输入头的数量：");
	scanf ("%d", &heads);
	printf ("请输入脚的数量：");
	scanf ("%d", &feet);
	
	int chicken, rabbit;
	for (chicken = 1; chicken < heads; chicken++)
		{
			for (rabbit = 1; rabbit < heads; rabbit++)
				{
					if (chicken  + rabbit == heads && 2 * chicken  + 4 * rabbit == feet)
						{
							printf ("鸡有%d只\n", chicken);
						    printf ("兔有%d只\n", rabbit); 
						}
				}
		}
	
	return 0;
}
```

### 水仙花数
```c

```

### tic-tac-toe
```c
#include <stdio.h>

int main(int argc, char const *argv[])
{
	const int size = 3;
	int board[size][size];
	int i,j;
	int numOfORow, numOfXRow, numOfOColumn, numOfXColumn, numOfOB, numOfXB, numOfOS, numOfXS;
	int result = -1; //-1：没人赢，1：X赢，0：O赢
	
	// 读入矩阵 
	for(i = 0; i < size; i++) {
		for(j = 0; j < size; j++) {
	    	scanf("%d", &board[i][j]); 
		}
	}
	for (i = 0; i < size && result == -1; i++) {
	    numOfORow = numOfXRow = numOfOColumn = numOfXColumn = numOfOB = numOfXB = numOfOS = numOfXS = 0;
	    for (j = 0; j < size; j++) {
	    	
	    	//检查行
	        if (board[i][j] == 1) {
	            numOfXRow++;
	        } else {
	            numOfORow++;
	        }
	        
	        //检查列
	        if (board[j][i] == 1) {
	            numOfXColumn++;
	        } else {
	            numOfOColumn++;
	        }
	        
	        //检查正对角线
	        if (board[i][i] == 1) {
	            numOfXB++;
	        } else {
	            numOfOB++;
	        }
	        
			//检查反对角线
	        if (board[i][size-i-1] == 1) {
	            numOfXS++;
	        } else {
	            numOfOS++;
	        }
	    }
	    
	    //判断胜负 
		if (numOfORow == size || numOfOColumn == size || numOfOB == size || numOfOS == size) {
		    result = 0;
		} else if (numOfXRow == size || numOfXColumn == size || numOfXB == size || numOfXS == size) {
		    result = 1;
		}
	}
	
	//输出结果	
	if (result == 1) {
		printf("X is winner.");
	} else if (result == 0)  {
		printf("O is winner.");
	} else if (result == 1) {
		printf("No winner.");
	}
	
	return 0;
}
```





