#### 과제 내용: 이 문제는 두개의 숫자를 입력받아 서로 더해 출력하는 과제이다. 얼핏 보면 매우 간단한 문제이지만 두개의 숫자 x,y 외에 세개의 수n,m,k를 더 입력 받는다. n,m,k는 자신이 원하는 진법(2~16)을 입력받는다. 자신이 원하는 진수의 숫자를 입력받아 더한 뒤 그 결과를 자신이 원하는 진법에 맞게 출력하는 프로그램이다.
---
```
import java.util.*;
public class NumeralSystem {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		int n, m, k;
		int x, y;
		int temp;
		int [] result = new int[100];
		int i = 0;
		Scanner input = new Scanner(System.in);
		
		System.out.print("n을 입력하시오: ");
		n = input.nextInt();
		System.out.print("x를 입력하시오: ");
		x = input.nextInt(n);
		
		System.out.print("m을 입력하시오: ");
		m = input.nextInt();
		System.out.print("y을 입력하시오: ");
		y = input.nextInt(m);
		temp = x+y;
		//System.out.println(x+y);
		System.out.print("k를 입력하시오: "); 
		k = input.nextInt();
		
		if (k < 10) {       //k가 10보다 작을 때 변화하여 출력
			while (temp > 0) {
				result[i] = temp % k;
				temp = temp / k;
				i ++;
			}
			System.out.print("x+y: ");
			i--;
			for (; i>=0; i--) {
				System.out.print(result[i]);
			}
		}
		
		else if ( k == 10) 
			System.out.print("x+y: " + temp);
		
		else if (k > 10) {        //k가 10보다 클때 변환하여 출력
			while (temp > 0) {
				result[i] = temp % k;
				temp = temp / k;
				i++;
				}
			System.out.print("x + y: ");
			i--;
			for (; i>=0; i--) {
				switch (result[i]) {
				case 10:
					System.out.print("a");
					break;
				case 11:
					System.out.print("b");
					break;
				case 12:
					System.out.print("c");
					break;
				case 13:
					System.out.print("d");
					break;
				case 14:
					System.out.print("e");
					break;
				case 15:
					System.out.print("f");
					break;
				default:
					System.out.print(result[i]);
					break;
				}	
			}			
		}
		input.close();
	}
}
```
---
#### 풀이과정 : 이 문제는 x,y를 scanner input으로 입력 받을때 괄호안에 숫자를 넣으면 그에 맞는 진법으로 입력을 가능하게 하고 입력을 받으면 자동으로 10진법으로 변환 되는것을 이용했다.
#### 따라서 입력받은 수를 더한 뒤 출력진법 k가 10진법이면 다른 변환없이 x+y를 출력하고, 10보다 작거나 크면 각 진법에 맞게 변환하여 출력하게 만들어 주었다. 





