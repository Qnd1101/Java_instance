# 😮자바 인스턴스 활용

### 부가가치세를 계산해주는 프로그램인데 메소드, 클래스, 인스턴스를 활용하여 코드를 더 간소화 시키는걸 코드를 보고 살펴보면 된다. 코드들이 계속해서 비슷하긴 하지만 코드를 보기 편하게 만드는 과정이라고 생각하시면 됩니다.
### 1단계 : [클래스], [메소드] 사용🍎
  * #### Accounting1[클래스]에서 valueOfSupply(공급가액)과  vatRate(부가가치세)를 선언하였다.
  * #### Accounting1[클래스]에서 부가가치세를 계산해서 main[메소드]로 반환 시켜주는 double type의 vatRate()[메소드]를 선언하였다.
  * #### Accounting1[클래스]에서 공급가액과 부가가치세 계산 결과를 main[메소드]로 반환 시켜주는 double type의 getTotal()[메소드]를 선언하였다.
  * #### AccountingApp1[클래스]에서 선언한 valueOfSupply을 main[메소드]에서 값을 넣고 출력을 한다. 
* #### 1단계의 단점(1) : 클래스의 기능과 메소드의 기능을 활용하여 코드를 작성하긴 했지만, 가시성과 가독성이 떨어진다.
* #### 1단계의 단점(2) : 작업 할 때마다 값을 바꿔주어야 하는 아주 귀찮고, 또 버그를 유발하는 행위를 하여야 한다. 
   	
### 1단계 Java Code
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
### 2단계 : [클래스], [인스턴스], [메소드] 사용 🍓
  * #### 1단계와 비슷하지만 2단계에서는 [인스턴스]변수를 생성하여 코드를 더 간소화 시킨다. 
  * #### AccountingApp2[클래스]의 main[메소드]에서 [인스턴스]를 생성하였는데 valueOfSupply와 getVAT()는 인스턴스에 소속된 변수이므로 Accounting2[클래스]에서 valueOfSupply를 1단계에서 'public static double valueOfSupply'라고 선언하였는데 static은 class의 소속 이므로 static을 지워 주어야 한다.(getVAT, getTotal 또한 마찬가지다.)
  * #### a1, a2 처럼 각자 독립적인 상태로 있기 때문에 1단계에서 값을 계속 바꿔주어야 한다는 불편함이 사라지고, [인스턴스]를 호출만 해주면 값을 가져올 수 있게 편하게 사용 할 수 있도록 작성하였다.

### 2단계 Java Code
```java
class Accounting2 {
	public double valueOfSupply;	// 인스턴스에 소속된 변수이므로 static을 지워 주어야 함
	// 공급가액
	public static double vatRate = 0.1;
	// 부가가치세율
	public double getVAT() {	// 인스턴스에 소속된 변수이므로 static을 지워 주어야 함
		return valueOfSupply * vatRate; 
	}
	public double getTotal() {	// 인스턴스에 소속된 변수이므로 static을 지워 주어야 함
		return valueOfSupply + getVAT();
	}
}
public class AccountingApp2 {
	public static void main(String[] args) {
		Accounting2 a1 = new Accounting2();  // 인스턴스 생성
		a1.valueOfSupply = 10000.0;
		
		Accounting2 a2 = new Accounting2();  // 인스턴스 생성
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
### 3단계 : [클래스], [생성자], [인스턴스], [매개변수], [this], [메소드] 사용
  * #### 1단계, 2단계와 비슷하지만 3단계에서는 [생성자], [매개변수], [this]를 사용하여 더 가독성을 높였다.
  * #### 2단계와는 다르게 괄호 안에 인자값을 전달한다.
```java
	Accounting3 a1 = new Accounting3(10000.0); 
	Accounting3 a2 = new Accounting3(20000.0);
```
  * #### 생성자를 간략하게 설명하자면
    * #### 생성자의 이름은 클래스 이름과 동일 하여야 한다.
    * #### 생성자는 객체가 생성될 떄 자동으로 한번 호출 된다.
    * #### 생성자는 매개변수 조건에 따라 여러개를 작성할 수 있다. (OverLoding)
   * #### 생성자 정의
```java
public Accounting3(double valueOfSupply) {
    this.valueOfSupply = valueOfSupply; 
    // this.valueOfSupply는 class에 있는 변수를 의미하고, valueOfSupply는 인자값(Parameter)이다.
}
```
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
