```java
package net.helloworld.demo;

public class Test {
	
	public static void main(String[] arg) {
		System.out.println("来说是非者，必是是非人");
	}
}

```

```java
package net.helloworld.demo;

public class Test {
	
	public static void main(String[] arg) {
		/*
		 * 块注释
		 * 介绍代码片段的功能
		 */
		//行注释
		System.out.println("来说是非者，必是是非人");
		
		//调运fun方法
		int i1=10;
		int i2=20;
		int i3=fun(i1,i2);
		System.out.println("方法的返回值是" + i3);//可以输出任意类型的数据
	}
	//比较两个数的大小
	public static int fun(int a,int b) {
		if(a>b) {
			return 1;
		}
		else if(a==b) {
			return 0;
		}
		else {
			return -1;
		}
	}
}

```

```java
		    int i,num=0,word=0,space=0,punc=0;
			for(i=1;str[i]!='\0';i++) {
				if(str[i]>=0&&str[i]<=9) {
					num++;
				}
				else if(str[i]>='a'&&str[i]<='z') {
					word++;
				}
				else if(str[i]>='A'&&str[i]<='Z') {
					word++;
				}
				else {
					punc++;
				}
			System.out.println("数字个数：" + num);
			System.out.println("英文字母个数：" + word);
			System.out.println("空格个数：" + space);
			System.out.println("其他字符个数：" + punc);
```

goto const不能作为关键字和保留符。

```java

import java.util.Scanner;

public class Main {
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		String a = sc.nextLine();
		char[] c = a.toCharArray();
		int n1=0;
		int n2=0;
		int n3=0;
		int n4=0;
		for(int i=0;i<a.length();i++)
		{
			if(c[i]>='a' && c[i]<='z')
				n1++;
			else if(c[i]>='0' && c[i]<='9')
				n2++;//一定要注意这里0，9都要打上单引号，如果没打，不会报错，但是会有逻辑错误，输出错误的结果。
			else if(c[i]==' ' )
				n3++;//这里也是，注意是单引号不能是双引号，双引号程序会报错，这里单引号内换成\t或者\u0009都会出现错误的结果
			else
				n4++;
		}
		System.out.print(n1+" "+n2+" "+n3+" "+n4);
	}
    
    
		
}

```

**要求在控制台输入一行字符，分别统计出其中英文字母、空格、数字和其他字符的个数。**

 

```java
//第1题 高昕 五班 2019012472
package net.helloworld.demo;

import java.util.Scanner;

public class Test{
	
	public static void main(String[] args) {
		
		System.out.println("请输入一串字符串：");
		Scanner scan  = new Scanner(System.in);
		String str1 =scan.nextLine();
		System.out.println("输入的数据为：" + str1);
		int i,num=0,word=0,space=0,punc=0;
		char[] str=str1.toCharArray();
		for(i=0;str[i]!='\0';i++) {
			if(str[i]>='0'&&str[i]<='9') {
				num++;
			}
			else if(str[i]>='a'&&str[i]<='z') {
				word++;
			}
			else if(str[i]>='A'&&str[i]<='Z') {
				word++;
			}
			else if(str[i]==' ') {
				space++;
			}
			else {
				punc++;
			}
		System.out.println("数字个数：" + num);
		System.out.println("英文字母个数：" + word);
		System.out.println("空格个数：" + space);
		System.out.println("其他字符个数：" + punc);
	}
   }
}

```

**某个公司采用加密的方式传递数据，已知该数据是四位的整数，加密的规则如下：每位数字都加上5，然后用和除以10的余数代替该数字，再将第一位和第四位数字交互，第二位和第三位交换。通过程序实现输入一个四位整数求出加密后的数据。** 

```java
//第2题 高昕 五班 2019012472
package net.helloworld.demo;

import java.util.Scanner;

public class Test{
	
	public static void main(String[] args) {
		System.out.println("四位数为：");
		Scanner data = new Scanner(System.in);
		int num = data.nextInt();
		int[] nums = new int[10];
		int temp;
		int i=0;
        nums[0]=num/1000;
        nums[1]=(num-nums[0]*1000)/100;
        nums[2]=(num-nums[0]*1000-nums[1]*100)/10;
        nums[3]=num-nums[0]*1000-nums[1]*100-nums[2]*10;
        for(i=0;i<4;i++) {
        	nums[i]=(nums[i]+5)%10;        
        }
        temp=nums[3];
        nums[3]=nums[0];
        nums[0]=temp;
        
        temp=nums[2];
        nums[2]=nums[1];
        nums[1]=temp;
        System.out.println("加密后的数据：");
        for(i=0;i<4;i++) {
        	System.out.print(nums[i]);
        }
        System.out.println();
        		
	}
}
```

**题目01_3**

学号数组：String[] stuNo = { "2019011500", "2019011501", "2019011502", "2019011503", "2019011504" }

姓名数组：String[] stuName = { "张三", "李四", "王五", "赵六", "王九" }

英语成绩数组：int[] englishScore = { 55, 79, 96, 68, 87 }

数学成绩数组：int[] mathScore = {90, 65, 78, 82, 50}

**学号姓名和两科成绩一一对应，也就是说学生张三的学号为2019011500，他的英语成绩是55，数学成绩是90。**        

**写Java程序，要求实以下现功能（提示：可以使用Arrays类中的方法sort()、copyOf()、toString()）：**

**（1）** **计算英语成绩数组中最大值、最小值、所有值之和，并输出到控制台。**

**（2）** **计算数学成绩的平均值，并输出到控制台。**

**（3）** **按照英语成绩从高到低，输出学生的姓名和学号。**

**（4）** **将学号按照从小到大排序，并复制数组内容到一个新的数组中。**

```java
//第3题 高昕 五班 2019012472
package net.helloworld.demo;

import java.util.Scanner;
import java.util.Arrays;
public class Test{
	
	public static void main(String[] args) {				
	    String[] stuNo = { "2019011500", "2019011501", "2019011502", "2019011503", "2019011504" };
		String[] stuName = { "张三", "李四", "王五", "赵六", "王九" };
		int[] englishScore = { 55, 79, 96, 68, 87 };
		int[] mathScore = {90, 65, 78, 82, 50};
		//计算英语成绩数组中最大值、最小值、所有值之和，并输出到控制台。
	    int englishmax,englishmin,englishsum = 0;	
	    int[] englishScore2 = Arrays.copyOf(englishScore,englishScore.length);
	    Arrays.sort(englishScore2);
	    englishmax = englishScore2[4];
	    englishmin = englishScore2[0];
	    for(int i=0;i<5;i++) {
	    	englishsum += englishScore[i];
	    }
	    System.out.println("英语成绩数组中：");
	    System.out.println("最大值="+ englishmax);
	    System.out.println("最小值="+ englishmin);
	    System.out.println("所有值之和="+ englishsum);
	    //计算数学成绩的平均值，并输出到控制台。
	    int mathaver,mathsum = 0,temp;
	    for(int i=0;i<5;i++) {
	    	mathsum += mathScore[i];
	    }
	    mathaver = mathsum / 5;
	    System.out.println("数学成绩的平均值="+ mathaver);
	    // 按照英语成绩从高到低，输出学生的姓名和学号。
	    int[] englishScore3 = Arrays.copyOf(englishScore,englishScore.length);
	    String chartemp;
	    System.out.println("按照英语成绩从高到低，输出学生的姓名和学号。");
	    for(int i = 0;i<5;i++) {
	    	for(int j=0;j<4;j++) {
	    		if(englishScore3[j]<englishScore3[j+1])
	    		{
	    			temp = englishScore3[j];
	    			englishScore3[j] = englishScore3[j+1];
	    			englishScore3[j+1] = temp; 
	    			
	    			chartemp = stuName[j];
	    			stuName[j] = stuName[j+1];
	    			stuName[j+1] = chartemp;
	    			
	    			chartemp = stuNo[j];
	    			stuNo[j] = stuNo[j+1];
	    			stuNo[j+1] = chartemp;
	    			
	    		}
	    	}
	    }
	    for(int k=0;k<5;k++) {
	    	System.out.println("姓名：" + stuName[k] + "     学号："+ stuNo[k]);
	    }
	    //（4） 将学号按照从小到大排序，并复制数组内容到一个新的数组中。
	    int[] stuno= {0,0,0,0,0};
	    for(int i=0;i<5;i++) {
	    	stuno[i]= Integer.parseInt(stuNo[i]);
	    }
	    for(int i=0;i<5;i++) {
	    	for(int j=0;j<4;j++) {
	    		if(stuno[j]>stuno[j+1]) {
	    			temp = stuno[j];
	    			stuno[j] = stuno[j+1];
	    			stuno[j+1] = temp;
	    		}
	    	}
	    }
	    System.out.println("将学号按照从小到大排序:");
	    for(int i=0;i<5;i++) {
	    	System.out.println(stuno[i]);
	    }
	    //复制数组
	  	int[] newstNo;
	  	newstNo =  Arrays.copyOf(stuno,stuno.length);
	  	
   }	
}
```

switch int short char byte 枚举类型 字符串类型；