**1**如何导入POI？

-  打开Eclipse
- 依次点击File->New->Java Project
- 输入项目名称，本例中设置为POI
- 单击完成
- 在项目上点击右键->New->Folder
- 输入文件夹名称lib
- 把刚才解压的poi-3.0.1-FINAL-20070705.jar复制过来
- 右键点击项目，选择Properties
- 在左侧列表里选中Java Build Path，右侧选中Libraries
- 点击Add JARs，选择POI项目的lib下的所有文件
- 两次OK确认，回到Eclipse界面

**小技巧，快捷操作：可以用鼠标左键选中poi-3.0.1-FINAL-20070705.jar但不松开，拖到任务栏的Eclipse图标上等候1秒左右，Eclipse会自动弹起来，依然不松开移动到lib文件夹上，这个时候鼠标后面跟个十字符号，松开左键，就完成了复制动作。这个是对整个windows系统都好用的快捷复制方式，视源盘符和目标盘符的不同偶尔会用到Ctrl键。 **

```java
package com.excel1.demo;

import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.math.BigDecimal;
import org.apache.poi.hssf.usermodel.HSSFCell;
import org.apache.poi.hssf.usermodel.HSSFRow;
import org.apache.poi.hssf.usermodel.HSSFSheet;
import org.apache.poi.hssf.usermodel.HSSFWorkbook;

public class Test {
	//读取函数
	public static double readExcel(int a,int b) {
		double num = 0;
		try {
			FileInputStream in = new FileInputStream("D:\\成绩单.xls");
			HSSFWorkbook workbook = new HSSFWorkbook(in);
			HSSFSheet sheet = workbook.getSheetAt(0);
			HSSFRow row = sheet.getRow(a);
			HSSFCell cell = row.getCell(b);			
						
			in.close();
			num = cell.getNumericCellValue();
			
		} catch (Exception e) {
			System.out.println("1出错了！");
			e.printStackTrace();
		}
		
		
		return num;
	}
	//写入函数
	public static void writeExcel(int a,int b,int num) {
		try {			
			FileInputStream in = new FileInputStream("D:\\成绩分析.xls");
			HSSFWorkbook wb = new HSSFWorkbook(in);
			HSSFSheet sheet = wb.getSheetAt(0);
			
			HSSFRow row1 = sheet.getRow(a);
			//HSSFRow row1 = sheet.createRow(a);
			HSSFCell cell1_1 = row1.createCell(b);
			cell1_1.setCellValue(num);			
			FileOutputStream out = new FileOutputStream("D:\\成绩分析.xls");
			wb.write(out);
			in.close();
			out.close();
			
		} catch (Exception e) {
			System.out.println("2出错了！");
			e.printStackTrace();
		}
	}
	public static void writeExcel(int a,int b,double num) {
		try {			
			FileInputStream in = new FileInputStream("D:\\成绩分析.xls");
			HSSFWorkbook wb = new HSSFWorkbook(in);
			HSSFSheet sheet = wb.getSheetAt(0);
			HSSFRow row1 = sheet.getRow(a);
			//HSSFRow row1 = sheet.createRow(a);
			HSSFCell cell1_1 = row1.createCell(b);
			cell1_1.setCellValue(num);			
			FileOutputStream out = new FileOutputStream("D:\\成绩分析.xls");
			wb.write(out);
			in.close();
			out.close();
			
		} catch (Exception e) {
			System.out.println("3出错了！");
			e.printStackTrace();
		}
	}
	public static void writeExcel2(int a,int b,double num) {
		try {			
			FileInputStream in = new FileInputStream("D:\\成绩分析.xls");
			HSSFWorkbook wb = new HSSFWorkbook(in);
			HSSFSheet sheet = wb.getSheetAt(0);
			//HSSFRow row1 = sheet.createRow(a);
			HSSFRow row1 = sheet.getRow(a);
			HSSFCell cell1_1 = row1.createCell(b);
			String numstr = String.valueOf(num) + "%";
			cell1_1.setCellValue(numstr);			
			FileOutputStream out = new FileOutputStream("D:\\成绩分析.xls");
			wb.write(out);
			in.close();
			out.close();
			
		} catch (Exception e) {
			System.out.println("3出错了！");
			e.printStackTrace();
		}
	}
	//主函数
	public static void main(String[] args) {
		
		int[] group = new int[5];
		double[] groupOf = new double[5];
		double average = 0,max = 0,min = 0,temp = 0;
		double[] nomalScore = new double[53];
		double[] testScore = new double[53];
		double[] lastScore = new double[53];
		double[] totalScore = new double[53];
		for(int i = 0,j=1;i < 53; i++,j++) {
			nomalScore[i] = readExcel(j,4);
		}
		
		for(int i = 0,j=1;i < 53; i++,j++) {
			testScore[i] = readExcel(j,5);
		}
		
		for(int i = 0,j=1;i < 53; i++,j++) {
			lastScore[i] = readExcel(j,6);
		}
		
		for(int i = 0;i < 53; i++) {
			totalScore[i] = nomalScore[i] * 0.05 + testScore[i] * 0.55 + lastScore[i] * 0.4 ;
			BigDecimal   b   =   new   BigDecimal(totalScore[i]);
			totalScore[i] = b.setScale(2,   BigDecimal.ROUND_HALF_UP).doubleValue();
			if(totalScore[i]>=90) {
				group[0]++;
			}else if(totalScore[i] >= 80 && totalScore[i] < 90) {
				group[1]++;
			}else if(totalScore[i] >= 70 && totalScore[i] < 80) {
				group[2]++;
			}else if(totalScore[i] >= 60 && totalScore[i] < 70) {
				group[3]++;
			}else if(totalScore[i] < 60){
				group[4]++;
			}
		}
		for(int i = 0;i < 5;i++) {
			groupOf[i] = group[i] / 53.0 * 100;
			BigDecimal   a   =   new   BigDecimal(groupOf[i]);
			groupOf[i] = a.setScale(2,   BigDecimal.ROUND_HALF_UP).doubleValue();

		}
		for(int i = 0;i < 53; i++) {
			average += totalScore[i];
			
		}
		
		average = average/53;
		BigDecimal   b   =   new   BigDecimal(average);
		average = b.setScale(2,   BigDecimal.ROUND_HALF_UP).doubleValue();
		for(int i =0;i < 53;i++) {
			for(int j = 0; j < 52;j++) {
				if(totalScore[j] <= totalScore[j+1] ) {
					temp = totalScore[j];
					totalScore[j] = totalScore[j+1];
					totalScore[j+1] = temp;
				}
			}
		}
		max = totalScore[0];
		min = totalScore[52];
		for(int i = 2,j = 0;i < 7;i++,j++) {
			writeExcel(1,i,group[j]);
		}
		for(int i = 2,j = 0;i < 7;i++,j++) {
			writeExcel2(2,i,groupOf[j]);
		}
		writeExcel(3,2,average);
		writeExcel(3,4,max);
		writeExcel(3,6,min);


	}

}

```

