**题目02_1**

​    **定义一个菜谱类Recipe用来存储某种菜的制作过程等相关信息，其属性包括：菜谱名称、菜系（如：川菜、湘菜等）、烹饪时长(分钟)、所需的多种食材(字符串数组类型，假设每种菜所需食材不会超过10种)、操作步骤，在main方法中定义一个数组存储5个菜谱的信息。**

​    **要求：**

**(1)**

**按名称模糊查询并输出符合条件的菜谱的所有信息，要求实现查找包含特定名称的菜谱信息的方法：searchRecipesContainName(Recipe[] recipes, String name)，例如：希望找到所有名称中包含牛肉的菜谱，可以使用字符串类String类的contains方法，来判断某个字符串中是否包含某个子串。**



**(2按菜系查询并输出符合条件的菜谱的所有信息，要求能够实现查找某个菜系的菜谱信息的方法：searchRecipes(Recipe[] recipes, String style)，例如：希望查找所有湘菜的菜谱（可以使用字符串类String类的equals方法，来判断某个字符串是否与指定字符串相同），输出格式同上。**

**(3查询烹饪时间小于某个时长的菜谱并输出，要求实现查找方法：searchRecipeLessThan(Recipe[] recipes, int time),例如：希望查找烹饪时长小于30分钟的菜谱，输出格式同上。**

**(4)查询包含某种食材的菜谱信息并输出，要求实现查找方法：searchRecipeContainsFood(Recipe[] recipes, String food),例如：希望查找包含西红柿的菜谱，输出格式同上。**

**提示：**

**(1)定义的菜谱类：包括属性、属性的getter、setter方法。**

**(2)类中其他方法可自由发挥，比如打印菜谱信息的方法（如print()或toString()）**

**(3)自己定义包含main方法的类，类中定义4个static方法，分别用来实现要求中规定的4个方法。**



```java
package com.recipes.demo;

public class Recipeclass {
	//成员属性：规范的定义用private
	private String name;
	private String style;
	private int time;
	private String[] material = new String[10];

	private String steps;
	
	//给私有属性提供getter\setter方法
	public void setName(String aName) {
		name= aName;
	}
	public String getName(){
		return name;
	}
	
	public void setStyle(String aStyle) {
		style= aStyle;
	}
	public String getStyle(){
		return style;
	}
	
	public void setTime(int aTime) {
		time=aTime;
	}
	public int getTime() {
		return time;
	}
	public void setMaterial(String[] bmaterial) {
		for(int i = 0;i<bmaterial.length;i++) {
			material[i]=bmaterial[i];
		}
	}
	public String getMaterial() {
		String str ="";
		for(int i = 0;i<10&&material[i]!=null;i++) {
			str = str + material[i];
		}
		return str;
	}
	
	public void setSteps(String aSteps) {
		steps= aSteps;
	}
	public String getSteps(){
		return steps;
	}
	//输出所有属性的值
	public  void allprint() {
		System.out.println("菜谱名称:"+name);
		System.out.println("菜系:"+style);
		System.out.println("时长:"+time);
		System.out.print("所需食材:");
		for(int i=0; i<10 && material[i]!=null;i++) {
			System.out.print(material[i]);
		}
		System.out.println("");
		System.out.println("操作步骤:"+steps);
	}
}

```

```java
package com.recipes.demo;

public class Recipe {
	
	public static void main(String[] args) {
		Recipeclass[] dish = new Recipeclass[5];
		
		
		dish[0]= new Recipeclass();
		dish[0].setName("酱牛肉");
		dish[0].setStyle("家常菜");
		dish[0].setTime(120);
		String[] bmaterial0 = new String[]{"牛腱子","黄豆酱","油","黄酒","冰糖"};
		dish[0].setMaterial(bmaterial0);
		dish[0].setSteps("1.准备好主要食材;2.加入食材慢炖两至三小时");
		
		dish[1]= new Recipeclass();
		dish[1].setName("红烧牛肉");
		dish[1].setStyle("家常菜");
		dish[1].setTime(120);
		String[] bmaterial1 = new String[]{"牛腩","牛筋","生抽","冰糖"};
		//dish[1].setMaterial("牛腩","牛筋","生抽","冰糖");
		//dish[1].setMaterial("牛腩牛筋生抽冰糖");
		dish[1].setMaterial(bmaterial1);
		dish[1].setSteps("1.准备好主要食材;2.加入食材慢炖两至三小时");
		
		dish[2]= new Recipeclass();
		dish[2].setName("毛血旺");
		dish[2].setStyle("川菜");
		dish[2].setTime(90);
		String[] bmaterial2 = new String[]{"豆芽","鸭血","白菜","豆腐"};
		//dish[2].setMaterial("豆芽","鸭血","白菜","豆腐");
		//dish[2].setMaterial("豆芽鸭血白菜豆腐");
		dish[2].setMaterial(bmaterial2);
		dish[2].setSteps("1.准备好主要食材;2.加入食材慢炖一至两小时");
		
		dish[3]= new Recipeclass();
		dish[3].setName("周黑鸭");
		dish[3].setStyle("湘菜");
		dish[3].setTime(90);
		String[] bmaterial3 = new String[]{"鸭肉","大料","麻椒","茶叶"};
		//dish[3].setMaterial("鸭肉","大料","麻椒","茶叶");
		//dish[3].setMaterial("鸭肉大料麻椒茶叶");
		dish[3].setMaterial(bmaterial3);
		dish[3].setSteps("1.准备好主要食材;2.加入食材慢炖一至两小时");
		
		dish[4]= new Recipeclass();
		dish[4].setName("西红柿炖鱼");
		dish[4].setStyle("湘菜");
		dish[4].setTime(25);
		String[] bmaterial4 = new String[]{"鱼肉","白菜","豆腐","辣椒","西红柿"};
		//dish[4].setMaterial("鱼肉","白菜","豆腐","辣椒","西红柿");
		//dish[4].setMaterial("鱼肉白菜豆腐辣椒西红柿");
		dish[4].setMaterial(bmaterial4);
		dish[4].setSteps("1.准备好主要食材;2.加入食材慢炖一小时");

		//第一问
		System.out.println("(1)找到所有名称中包含牛肉的菜谱:");
		searchRecipesContainName(dish, "牛肉");
		//第二问
		System.out.println("(2)查找所有湘菜的菜谱:");
		searchRecipes(dish, "湘菜");
		//第三问
		System.out.println("(3)烹饪时间小于90分钟的菜谱并输出:");
		searchRecipeLessThan(dish, 90);
		//第四问
		System.out.println("(4)查找包含西红柿的菜谱");
		searchRecipeContainsFood(dish, "西红柿");
	}
	
	
	public static void searchRecipesContainName(Recipeclass[] recipes, String name) {
		for(int i = 0;i <= recipes.length-1;i++) {
			if(recipes[i].getName().contains(name)) {
				recipes[i].allprint();				
				System.out.println();
			}
		}
	}

	
		
	public static void searchRecipes(Recipeclass[] recipes, String style) {
		for(int i = 0;i <= recipes.length-1;i++) {
			if(recipes[i].getStyle().equals(style)) {
				recipes[i].allprint();				
				System.out.println();
			}
		}		
	}
	
	public static void searchRecipeLessThan(Recipeclass[] recipes, int time) {
		for(int i = 0;i <= recipes.length-1;i++) {
			if(recipes[i].getTime() < time) {
				recipes[i].allprint();			
				System.out.println();
			}
		}				
	}
	public static void searchRecipeContainsFood(Recipeclass[] recipes, String food) {
		for(int i = 0;i <= recipes.length-1;i++) {
			if(recipes[i].getMaterial().contains(food)) {
				recipes[i].allprint();			
				System.out.println();		
	        }
	    }
    }
}
```

**题目02_2**

 **定义一个复数类Complex类，该类需要满足以下条件：realPart表示复数的实数部分，imaginaryPart表示复数的虚数部分。**

 **在该类中除了属性的getter、setter方法之外，还需要实现以下方法：**

  **(1)**  **一个Complex add(Complex anotherComplex)方法，将当前复数对象与形参复数对象相加，所得的结果仍然是一个复数值，返回给该方法的调用者。**

  **(2)一个Complex addAnther(int anotherReal, int anotherImaginary)方法，将当前复数对象与形参的实数和虚数部分表示的复数对象相加，所得结果仍然是一个复数，返回给该方法的调用者。**

  **(3)编写一个测试类，在main方法中创建两个复数1+2i和3+4i，并显示它们的和。**

```java
package com.complexwork.demo;

public class Complex {
	private int realPart;
	private int imaginaryPart;
	
	public void setRealPart(int realPart0){
		realPart = realPart0;
	}
	
	public int getRealPart() {
		return realPart;
	}
	
	public void setImaginaryPart(int imaginaryPart0){
		imaginaryPart = imaginaryPart0;
	}
	
	public int getImaginaryPart() {
		return imaginaryPart;
	}
	
	Complex add(Complex anotherComplex) {
		int num=0,i=0;
		num = realPart+anotherComplex.realPart;
		i = imaginaryPart+anotherComplex.imaginaryPart;
		Complex anotherComplex2 = new Complex();
		anotherComplex2.realPart = num;
		anotherComplex2.imaginaryPart = i;
		System.out.println(num+"+"+i+"i");
		return anotherComplex2;
	}
	
	Complex addAnther(int anotherReal, int anotherImaginary) {
		Complex anotherComplex = new Complex();
		int num=0,i=0;
		num = realPart + anotherReal;
		i = imaginaryPart + anotherImaginary;
		anotherComplex.realPart = num;
		anotherComplex.imaginaryPart = i;
		System.out.println(num+"+"+i+"i");
		return anotherComplex;
	}
	
	
	
}

```



```java
package com.complexwork.demo;

public class Test {
	public static void main(String[] args) {
		
		Complex[] complex = new Complex[3];
		
		complex[0] = new Complex();
		complex[0].setRealPart (1);
		complex[0].setImaginaryPart(2);
		
		complex[1] = new Complex();
		complex[1].setRealPart (3);
		complex[1].setImaginaryPart(4);
		
		complex[2] = new Complex();
		complex[2].setRealPart (0);
		complex[2].setImaginaryPart(0);
		//第一问
		complex[0].add(complex[2]);
		//第二问
		complex[2].addAnther(3, 4);
		//第三问
		System.out.println("创建两个复数1+2i和3+4i，并显示它们的和:");
		complex[0].add(complex[1]);
		
	}
}

```

**阅读String类的源码，分析String类中equals方法和indexOf方法的具体实现流程，并谈谈自己的理解。**

```java
   public boolean equals(Object anObject) {
        if (this == anObject) {
            return true;
        }
        if (anObject instanceof String) {
            String anotherString = (String)anObject;
            int n = value.length;
            if (n == anotherString.value.length) {
                char v1[] = value;
                char v2[] = anotherString.value;
                int i = 0;
                while (n-- != 0) {
                    if (v1[i] != v2[i])
                        return false;
                    i++;
                }
                return true;
            }
        }
        return false;
    }
分析equals方法：
	1.比较此字符串和指定的字符串内存地址如果相同则返回值为真
	2.instanceof 是 Java 的保留关键字。它的作用是测试它左边的对象是否是它右边的类的实例。
	3.如果指定的字符串是否是字符串类则创建另一个字符串并将指定的字符串的值赋给创建的另一个字符串；
	4.anObject表示需要比较的字符串，value也就是当前字符串this。String.length()的内部实现就是value.length。定义n，n为此字符串的长度；
	5.判断此字符串的长度是否等于指定的字符串的长度。如果相等则
	创建字符类型的数组v1并将此字符串的每个字符按顺序储存在v1中；
	创建字符类型的数组v2并将创建另一个字符串的每个字符按顺序储存在v1中；
	利用循环判断是否此字符串和指定的字符串的每个字符的顺序是否相同
	如果相同则返回真，此字符串和指定的字符串相等；
	如果不相同则返回假，此字符串和指定的字符串不相等；
理解：
	先判断两字符串是不是同一地址，同一个字符串必然相同。若不是同一地址则先判断目标是不是字符串类型，若是则判断两字符串长度是否相同，若相同复制目标字符串到新字符串并分割为字符型数组，并按顺序逐个判断每个字符是否相同。
 
```

```java

    static int indexOf(char[] source, int sourceOffset, int sourceCount,
            char[] target, int targetOffset, int targetCount,
            int fromIndex) {
        if (fromIndex >= sourceCount) {
            return (targetCount == 0 ? sourceCount : -1);
        }
        if (fromIndex < 0) {
            fromIndex = 0;
        }
        if (targetCount == 0) {
            return fromIndex;
        }

        char first = target[targetOffset];
        int max = sourceOffset + (sourceCount - targetCount);

        for (int i = sourceOffset + fromIndex; i <= max; i++) {
            /* Look for first character. */
            if (source[i] != first) {
                while (++i <= max && source[i] != first);
            }

            /* Found first character, now look at the rest of v2 */
            if (i <= max) {
                int j = i + 1;
                int end = j + targetCount - 1;
                for (int k = targetOffset + 1; j < end && source[j]
                        == target[k]; j++, k++);

                if (j == end) {
                    /* Found whole string. */
                    return i - sourceOffset;
                }
            }
        }
        return -1;
    }
fromIndex：开始查找的位置、索引位置
sourceCount：源字符串长度
targetCount：查找字符串的长度
源字符串source
targetOffset：目标字符串偏移
分析indexOf方法：
	1.如果开始查找的位置大于源字符串长度，则再判断要查找字符串的长度是否为0，若为0则返回源字符串长度，若不为0则返回-1；
	2.如果开始查找的位置小于0，则把开始查找的位置设置的整型值为0；
	3.如果要查找字符串的长度为0，则返回开始查找的位置的整型值；
	4.创建一个字符first并赋值为要查找字符串的第一个字符；
	5.创建一个max表示可能查找到要查找字符串的第一个字符的最大长度的位置；
	6.利用循环，如果源字符串中的字符与要查找字符串的第一个字符不相等，则继续查找下一个，最后得到一个i的值；
	7.判断i是否小于等于可能查找到要查找字符串的第一个字符的最大长度的位置，如果是则判断要查找字符串的第二个字符是否与源字符串中i位置的下一个位置j的字符是否相等，若还相等则继续执行循环至j小于剩下的要查找字符串的长度；
	8.如果所有的要查找字符串的字符都再源字符串中找到，则返回要查找字符串出现在源字符串中的位置。
	9.其他情况都返回-1；
    /**
     * Returns the index within this string of the last occurrence of the
     * specified substring.  The last occurrence of the empty string ""
     * is considered to occur at the index value {@code this.length()}.
     *
     * <p>The returned index is the largest value <i>k</i> for which:
     * <blockquote><pre>
     * this.startsWith(str, <i>k</i>)
     * </pre></blockquote>
     * If no such value of <i>k</i> exists, then {@code -1} is returned.
     *
     * @param   str   the substring to search for.
     * @return  the index of the last occurrence of the specified substring,
     *          or {@code -1} if there is no such occurrence.
     */
分析indexOf方法：
	
```

 

















