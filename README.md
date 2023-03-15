# 😮자바 인스턴스 활용

### 부가가치세를 계산해주는 프로그램인데 복잡한 내용을 간소화 시켰다고 보면 된다.
* ### 1단계 : 클래스를 활용하여 
* ### 2단계 :   
* ### 3단계 :
![3월 15일 과제](https://user-images.githubusercontent.com/107795830/225227073-83b34431-3c52-4b6c-beca-a9a2860c3045.png)

### 1단계 java
```java
class Accounting1 {
	public static double valueOfSupply;
	public static double vatRate = 0.1;
	public static double getVAT() {
		return valueOfSupply * vatRate;
	}
	public static double getTotal() {
		return valueOfSupply + getVAT();
	}
}
public class AccountingApp1 {
	public static void main(String[] args) {
		Accounting1.valueOfSupply = 10000.0;
		System.out.println("Value of supply : " + Accounting1.valueOfSupply);
		Accounting1.valueOfSupply = 20000.0;
		System.out.println("Value of supply : " + Accounting1.valueOfSupply);
		
		Accounting1.valueOfSupply = 10000.0;
		System.out.println("VAT : " + Accounting1.getVAT());
		Accounting1.valueOfSupply = 20000.0;
		System.out.println("VAT : " + Accounting1.getVAT());
		
		Accounting1.valueOfSupply = 10000.0;
		System.out.println("Total : " + Accounting1.getTotal());
		Accounting1.valueOfSupply = 20000.0;
		System.out.println("Total : " + Accounting1.getTotal());
		
	}
}
```

### 2단계
```java
class Accounting2 {
	public double valueOfSupply;
	public static double vatRate = 0.1;
	public double getVAT() {
		return valueOfSupply * vatRate;
	}
	public double getTotal() {
		return valueOfSupply + getVAT();
	}
}
public class AccountingApp2 {
	public static void main(String[] args) {
		Accounting2 a1 = new Accounting2();
		a1.valueOfSupply = 10000.0;
		
		Accounting2 a2 = new Accounting2();
		a2.valueOfSupply = 20000.0;
		
		System.out.println("Value of supply : " + a1.valueOfSupply);
		System.out.println("Value of supply : " + a2.valueOfSupply);
		
		System.out.println("VAT : " + a1.getVAT());
		System.out.println("VAT : " + a2.getVAT());
		
		System.out.println("Total : " + a1.getTotal());
		System.out.println("Total : " + a2.getTotal());
		
	}
}
```

### 3단계
```java
class Accounting3 {
	public double valueOfSupply;
	public static double vatRate = 0.1;
	public Accounting3(double valueOfSupply) {
		this.valueOfSupply = valueOfSupply;
	}
	public double getVAT() {
		return valueOfSupply * vatRate;
	}
	public double getTotal() {
		return valueOfSupply + getVAT();
	}
}
public class AccountingApp3 {
	public static void main(String[] args) {
		Accounting3 a1 = new Accounting3(10000.0);
		
		Accounting3 a2 = new Accounting3(20000.0);
		
		System.out.println("Value of supply : " + a1.valueOfSupply);
		System.out.println("Value of supply : " + a2.valueOfSupply);
		
		System.out.println("VAT : " + a1.getVAT());
		System.out.println("VAT : " + a2.getVAT());
		
		System.out.println("Total : " + a1.getTotal());
		System.out.println("Total : " + a2.getTotal());
		
	}
}
```
