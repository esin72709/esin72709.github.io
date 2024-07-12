##### 01.조건문(Confitional statement)
> 조건문은 조건에 따라 프로그램을 수행하기 위해 사용함
> 관계 연산자와 함께 사용되며, if, switch 문이 대표적임
>
>프로그램에서 입력을 받아 입력된 값에 따라 동작을 다르게 하거나 특정 조건에 따라 처리되도록 하는 경우 조건문을 사용한다고 볼 수 있음
>
>대표적인 조건문은 if
>다양한 조건 구성을 위해 if ~ else if 등이 사용
>또 다른 조건문 switch
>switch문은 조건값에 따라 수행 블럭을 구분해서 정의할 수 있음
>3항 연산과 같이 참/거짓에 따른 간단한 조건 연산을 수행할 수 있는 구문도 존재

**if문**
> 조건에 따라 코드 블럭을 수행함

        if(조건식)	{
		        실행 코드 블럭
		}
- 수행 문장이 하나라면 중괄호 {}을 생략가능
- 수행조건은 관계연산가 논리연산의 조합을 통해 설정 가능
- 조건에 따라 처리를 다르게 하기 위해서는 if ~ else if 문을 사용함
- 단순 if문을 나열해 사용하는 것은 바람직하지 않음
- if 블럭 안에 또 다른 if 블럭의 사용이 가능함

**switch**
> 조건값에 따른 처리 블럭을 구분해서 처리할 수 있도록 구조화한 구문으로 상황에 따라 if ~ else if문의 대체가 가능함

    switch(입력 변수) {
	    case 조건값 : 실행 구문; break;
	    ...
	    defalut: 기본 실행 구문;
	}
+ 입력 변수는 정수형, 문자 혹은 문자열
+ 실행 구문은 별도의 {} 없이 구문을 나열해 사용
+ 실행 구문의 마지막에 반드시 break:를 넣어야 함, 그렇지 않으면 이후 조건의 구문들도 실행됨
+ defalut는 조건에 해당하는 입력값이 없는 경우 실행되는 코드를 기술함
+ 입력 변수의 값과 매칭되는 경우 수행하는 코드를 지정하는 것으로 복잡한 조건 체크는 한계가 있음

**3항연산**
> 간단하게 구현할 수 있는 조건문으로 비교적 간단한 if ~ else 구문 처리에 적합합니다.

    String result = (login)? "로그인 성공" : "로그인 실패";

**실습 : 조건문 기본 실습 예제**
> switch 문을 이용해 메뉴를 선택하고 선택한 메뉴에 따라 기능을 실행함
> 각가의 메뉴 실행 과정에서 if문과 3항 연산이 사용

    import java.util.Scanner;
    
    public class Conditional {
		    void login() {
				    Scanner scan = new Scanner(System,in);
				    
				    System.out.print("## 아이디를 입력하세요. : ");
				    String uname = scan.next();
				    
				    System.out.print("# 비밀번호를 입력하세요 : ");
				    String pwd = scan.next();
				    
				    if(uname.equals("hong") && pwd.equals("1234")) {
					    System.out.println("인증 확인 !! -> 로그인 성공");
					}
					
				else {
					System.out.println("아이디나 비밀번호가 틀렸습니다.");
			    }
			}
			
			void check() {
					int cnt = 10;
					String msg = cnt > 0? "새로운 쪽지가 있습니다.!!" : "새로운 쪽지가 없습니다.";
					System.out.println(msg);
			}
			
			public static void main(String[] args) {
					Conditional con = new Conditional();
					
					while(true) {
						System.out.printf("# 메뉴를 선택하세요 (1 : 로그인, 2 : 쪽지확인, x : 종류) ==>"); 
						Scanner scan = new Scanner(System.in);
						String sel = scan.next();
						
						switch(sel) {
								case "1" : con.login();break;
								case "2" : con.check();break;
								case "x" : System.exit(0);
								defalut : System.out.println("잘못된 입력입니다!");
					}
				}	
			}
		}

+ 로그인 메뉴는 아이디와 비밀번호를 입력받고 if 문을 이용해 주어진 값과 맞는지 확인
+ 쪽지 확인인 경우 cnt 변수값에 따라 3항연산을 이용해 출력할 메시지를 결정
+ x는 프로그램 종료, 이외 값 입력 시 잘못된 입력 출력
