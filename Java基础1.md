```java
package net.onest.demo;

import java.util.Scanner;

public class Test {

	public static void main(String[] args) {
		//可以输出任意类型的数据
		System.out.println(true);
		System.out.print(100);
		System.out.println();//输出一个换行符
		
		System.out.printf("%d",100);//整型
		System.out.println();//输出一个换行符
		System.out.printf("%c", 'a');//字符
		System.out.println();//输出一个换行符
		System.out.printf("%f", 10.0f);//float
		System.out.println();//输出一个换行符
		System.out.printf("%.2f", 100.0);//double
		System.out.println();//输出一个换行符
		System.out.printf("%s", "字符串");//字符串
		System.out.println();//输出一个换行符
		//System.out输出流
		
		//创建Scanner类型的对象
		//System.in输入流
		Scanner scan = new Scanner(System.in);
		
//		int n1 = scan.nextInt();//获取int类型数据
//		System.out.println("获取到的整型值是：" + n1);
		
//		double d1 = scan.nextDouble();//获取double类型数据
//		System.out.println("获取到的double数据值是：" + d1);
	
		//next()、nextLine()注意区分（获取字符串数据）
//		String str1 = scan.nextLine();//获取一行
//		String str1 = scan.next();
//		int n2 = scan.nextInt();
//		int n3 = scan.nextInt();
//		System.out.println("获取到的字符串值：" + str1);
//		System.out.println("n2=" + n2 + ";n3=" + n3 );
		
		//定义byte类型
		byte b1 = 12;
		
//		float f1 = 10.0;//编译不通过
		float f2 = (float)10.0;//强制类型转换，可能会损失精度
		
		char c = '我';
		
		System.out.println((int)'B');
		
		int n = 2;
		if(n == 2) {
			System.out.println(n);
		}
		boolean b2 = false;
	}
}
```

```java
package net.onest.demo;

import java.util.Scanner;

public class Test {

	public static void main(String[] args) {
		//定义常量
		final int NUM = 10;
		final int MAX_SIZE ;
		MAX_SIZE = 20;
		
		String str = "我是一个字符串";
		System.out.println(str instanceof String);
		
		int x = 2, y = 5;
		boolean bo =  1/x > (x+y) ;
		//&&当第一个操作数是false,出现短路现象
		//||当第一个操作数是true，出现短路现象
		if(x!=0 && ( 1/x > (x+y) )) {
			System.out.println("成立");
		}
		
		if(x == 2 || (x++) > y) {
			System.out.println("1");
		}
		System.out.println(x);
		
		//两个数中较小的
		int res = (x < y) ? x : y;
		System.out.println("两个数中较小是"+res);
		
		//负号-运算符
		int i = x + -y;
		System.out.println("运算结果"+i);
		
		//有符号数的右移
		int n = -1;
		System.out.println(n >> 1);//有符号右移，高位补符号位
		System.out.println(n >>> 1);//无符号右移，高位都补0
		
		n = 1;
		System.out.println(n << 1);//
		

		x *= y += x * y;
		System.out.println("x:" + x + " y:" + y);
		
		double f = 10.0;
		int a = (int)f;
		System.out.println("a:" + a);
		
		float f1 = x;
		
		Scanner sc = new Scanner(System.in);
		System.out.println("请输入成绩等级");
//		String s = sc.next();
//		switch(s) {
//		case "A":
//			System.out.println("你的成绩在90分以上");
//			break;
//		case "B":
//			System.out.println("你的成绩在70-90之间");
//			break;
//		case "C":
//			System.out.println("你的成绩在60-70之间");
//			break;
//		case "D":
//			System.out.println("你的成绩不及格");
//			break;
//		default:
//			System.out.println("你的输入不合法");
//			break;		
//		}
		
		for(int j = 0; j < 10; j++) {
			if(j == 5) {
//				break;//跳出循环
				continue;//结束本次循环，进入下一次循环
			}
			System.out.println(j);
		}
		
	}
}
```

数组

```java
package com.onest.demo;

import java.util.Arrays;

public class ArrayTest {

	public static void main(String[] args) {
		//定义数组:静态初始化
		int[] nums = {10,20,30,40};//在同一行
//		String[] strs;
//		strs = {"aaa","bbb"."ccc"};
//		int[2] nums1;
		int i;
		
		float[] fs = {10.0f, 15.0f,23.0f};//数组名.length数组长度
		System.out.println(fs.length);
		
		//动态初始化
		int[] nums1 = new int[5];
		for(int n : nums1) {//数组元素的默认值
			System.out.println(n);
		}
		nums[0] = 10;
		nums[1] = 30;
		for(int j = 0; j < nums1.length; j++) {
			nums1[j] = j * 10;
		}
		
		//静态初始化二维数组
		int[][] nums2 = {{1,2},{3,4,5} ,{6,7,8,9}};
		for(int m = 0; m < nums2.length; m++) {
			for(int n = 0; n < nums2[m].length; n++) {
				System.out.println(nums2[m][n]);
			}
		}
		//动态初始化二维数组
		int[][] nums3 = new int[3][4];
		int[][] nums4 = new int[3][];
		nums4[0] = new int[2];
		nums4[1] = new int[3];
		nums4[2] = new int[4];
		
		//排序
		int[] nums5 = {23,34,42,18,5,78,56};
		Arrays.sort(nums5);//调用静态方法（类名.方法名()）
		System.out.println(Arrays.toString(nums5));
	}
}

```

