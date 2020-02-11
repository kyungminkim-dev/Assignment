#### 과제 내용 : 이문제는 n을 입력받아 1부터 n까지의 합을 구하는 문제이다. 특이한 점은 입력받는 숫자 n이 자바가 입력받을 수 있는 자료형의 범위를 넘는 수를 입력받고 1부터 n까지의 합을 구한다는것이다.
---
```
import java.util.*;
public class Sigma {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Scanner input = new Scanner(System.in);
		String x;
		
		System.out.print("정수를 입력하시오: ");
		x = input.next();
		ArrayList<Integer> list1 = new ArrayList<Integer>();
		ArrayList<Integer> list2 = new ArrayList<Integer>();
		
		String y ="";
		
		for (int i=0; i<x.length();i++) {
			y += "9";
		}
		if (x.equals(y) ) {
			ArrayList<String> nineList1 = new ArrayList<String>();
			ArrayList<String> nineList2 = new ArrayList<String>();
			
			System.out.print(1+"+"+2+"+"+3+"+"+"..."+"+"+x+": ");
			
			nineList1.add("4");   //System.out.print(4);
			if (x.length() >=2) {
				for(int i=0; i<x.length()-1; i++) {
					nineList1.add("9");//System.out.print(9);
				}
				nineList1.add("5");//System.out.print(5);
				for(int j=0; j<x.length()-1; j++) {
					nineList1.add("0");//System.out.print(0);
				}
			}
			else {
				nineList1.add("5");//System.out.print(5);
			}
			Collections.reverse(nineList1);
			for (int i=0; i<nineList1.size(); i++) {
				if (i % 3 ==0) {
					nineList2.add(",");
				}
				nineList2.add(nineList1.get(i));
			}
			//System.out.println(nineList2);
			for(int i=nineList2.size()-1; i>=1; i--) {
				System.out.print(nineList2.get(i));
			}
		}
		
		else  {
			for (int i=0; i<x.length(); i++) {
				//System.out.println(x.substring(i,i+1));
				list1.add(Integer.parseInt(x.substring(i,i+1)));
				list2.add(Integer.parseInt(x.substring(i,i+1)));
		}
		
			Collections.reverse(list1);
			Collections.reverse(list2);
			
			
			list2.set(0, list2.get(0)+1);  //입력받은수 +1 
			
			for (int i=0; i<list2.size(); i++) {  //+1 했을때 올림수 처리
				if (list2.get(i) >= 10) {
					list2.set(i, 0);
					list2.set(i+1, list2.get(i+1)+1);		
				}
			}
			
			//System.out.println(list1);
			//System.out.println(list2);
			
			int size1 = list1.size();
			int size2 = list2.size();
			int [] mulList = new int[size1 + size2+1];
			
			//ArrayList<Integer> mulList = new ArrayList<Integer>();
			
			//mulList 배열 생성 : list1 * list2 후 저장
			for (int i=0; i<size1 ; i++) {
				for (int j=0; j<size2; j++) {
					int k = size1+size2-i-j;
					mulList[k] += list1.get(i)*list2.get(j);
					if (mulList[k] > 9) {
						mulList[k-1] += mulList[k]/10;	
						mulList[k] %= 10;
					}
				}
			}
			
			// mulList2 : 배열 타입인 mulList를 Arraylist로 바꿔줌
			ArrayList<Integer> mulList2 = new ArrayList<Integer>();
			
			for (int i=0; i<mulList.length; i++) {
				mulList2.add(mulList[i]);
			}
		
			//mulList3 : 두수의 곱을 저장하는 mulList2를 2로 나누어 mulList3에 저장 
			ArrayList<Integer> mulList3 = new ArrayList<Integer>();
			for (int i=0; i < mulList2.size(); i++) {
				if (mulList2.get(i) == 2) {
					mulList3.add(1);
					
				}
				else if (mulList2.get(i) == 0) {
					mulList3.add(0);
					
				}
				else if (mulList2.get(i) == 1 ) {
					mulList3.add(0);
					mulList2.set(i+1, mulList2.get(i+1) +10);
					
				}
				else if(mulList2.get(i) % 2 ==0 ) {
					mulList3.add(mulList2.get(i) / 2);
					
				}
				else if(mulList2.get(i) % 2 !=0 ) {
					mulList3.add(mulList2.get(i) / 2);
					mulList2.set(i+1, mulList2.get(i+1) +10);
				}
				
			}
			
			//System.out.println(mulList2);
			//System.out.println(mulList3);
			
			Collections.reverse(mulList3);
			
			ArrayList<String> mulList4 = new ArrayList<String>();
			for (int i=0; i<mulList3.size(); i++) {
				if ( i % 3 ==0) {
					mulList4.add(",");
				}
				mulList4.add(Integer.toString(mulList3.get(i)));
			}
			Collections.reverse(mulList4);
			//System.out.println(mulList4);
			
			int value =0;
			for (int i=0; i < mulList4.size(); i++) {
				if(!mulList4.get(i).equals("0") && !mulList4.get(i).equals(",")) {
					value += i;
					break;
				}
			}
			System.out.print(1+"+"+2+"+"+3+"+"+"..."+"+"+x+": ");
			for (int i=value; i<mulList4.size()-1; i++) {
				System.out.print(mulList4.get(i));
			}
		}
			
	}
	
}
```
---
#### 문제 풀이 : 이문제를 풀때는 입력받는 수를 문자열로 받은 뒤 그 문자열을 하나씩 배열에 저장한다. 이후 1부터 n까지의 합을 구하는 공식인 n*(n+1) / 2 를 이용하여 답을 구한다. 
