# 😮자바 인스턴스 활용

### 부가가치세를 계산해주는 프로그램인데 메소드, 클래스, 인스턴스를 활용하여 코드를 더 간소화 시키는걸 코드를 보고 살펴보면 된다.
* ### 1단계 : [클래스], [메소드] 사용🍎
   * #### 1. Accounting1[클래스]에서 valueOfSupply(공급가액)과  vatRate(부가가치세)를 선언하였다.
   * #### 2. Accounting1[클래스]에서 부가가치세를 계산해서 main[메소드]로 반환 시켜주는 double type의 vatRate()[메소드]를 선언하였다.
   * #### 3. Accounting1[클래스]에서 공급가액과 부가가치세 계산 결과를 main[메소드]로 반환 시켜주는 double type의 getTotal()[메소드]를 선언하였다.
   * #### 4. AccountingApp1[클래스]에서 선언한 valueOfSupply을 main[메소드]에서 값을 넣고 출력을 한다. (클래스의 기능과 메소드의 기능을 활용하여 코드를 작성하긴 했지만, 가시성과 가독성이 떨어진다.)
   
   	
### 1단계 java
```java
class Accounting1 {
	public static double valueOfSupply;
	// 공급가액
	public static double vatRate = 0.1;
	// 부가가치세율
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
* ### 2단계 : 
### 2단계 Java Code
```java
class Accounting2 {
	public double valueOfSupply;
	// 공급가액
	public static double vatRate = 0.1;
	// 부가가치세율
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
* ### 3단계 :

### 3단계 Java Code
```java
class Accounting3 {
	public double valueOfSupply;
	// 공급가율
	public static double vatRate = 0.1;
	//
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
