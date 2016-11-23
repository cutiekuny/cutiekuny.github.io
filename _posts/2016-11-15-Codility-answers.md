I made this codes by Java.
If you are interested in this questions, you can find more in here -> https://codility.com/

11-23 modified

```
### Q1> BinaryGap


class Solution {
    public int solution(int N) {
        // write your code in Java SE 8
        int i;
	    int count = 0, tmp1=0, tmp2=0, chk=0;

	    for(i=0; N>0 ; i++){
	    	tmp2 = N%2;
	    	if(tmp2 == 1){
	    	   chk = 1; 
	    	}
	    	if(chk == 1){
    	    	if(tmp2==0){
    	    	    count++;
    	    	}else{
    	    	    if(tmp1<count){
        	    	    tmp1 = count;
    	    	    }
    	    	    count = 0;   
    	    	}
	    	}
	    	N = N/2;
	    }
	    return tmp1;
    }
}


reference.
http://abh0518.net/tok/?p=535

### Q2-1> CyclicRotation
<code>
class Solution {
    public int[] solution(int[] A, int K) {
        final int MAX = 100;
	        final int MIN = 0;
	        int j;
	        int l = A.length;
	        if( l == 1 || l > MAX || l <= MIN || K > MAX || K <= MIN){ return A; }
	        K=K%l;
	        int[] B = new int [l];
            for( j=0; j<l; j++ ){
            	if( j+K < l ){
            		B[j+K] = A[j];
            	}else{
            		B[j+K-l] = A[j];
            	}
            }
	        return B;
    }
}
</code>

### Q2-2> OddOccurrencesInArray

reference
http://jays1204.github.io/node.js/codillity/2016/01/10/OddOccurrencesInArray.html

### Q3-1> TapeEquilibrium

<code>
class Solution {
    public int solution(int[] A) {
        // write your code in Java SE 8
        int i, j, k, l=0;
        k = A.length;
        int[] B = new int[A.length];
        int[] C = new int[A.length+1];
        B[0] = 0;
        C[k] = 0;
        for(i=1; i<k; i++){
            B[i] = B[i-1] + A[i-1];
            C[k-i] = C[k-i+1] + A[k-i];
        }
        for(i=1; i<k; i++){
            B[i] = B[i] - C[i];
            // |x|
            if(B[i]<0){
                B[i] = -B[i];
            }
            // minimal value
            if(B[i]<l || i==1){
                l = B[i];
            }
        }
        return l;
    }
}
</code>

### Q3-2> FrogJmp

<code>
class Solution {
    public int solution(int X, int Y, int D) {
        return (Y-X)%D == 0 ? (Y-X)/D : (Y-X)/D + 1;
    }
}
</code>

### Q3-3> PermMissingElem

<code>
class Solution {
    public int solution(int[] A) {
        int i=1, j=0, k;
        for(k=1; k<A.length+1; k++){
            i=i+k+1;
            j=j+A[k-1];
        }
        return i-j;
    }
}
</code>

### Q4-1> MissingInteger

<code>
import java.util.HashSet;
class Solution {
    public int solution(int[] A) {
        HashSet<Integer> set = new HashSet<>();
        for(int i=0; i<A.length; i++){
        	if(A[i]>0){
        		set.add(A[i]);
        	}
        }
        for(int i=1; i<Integer.MAX_VALUE; i++){
        	if(!set.contains(new Integer(i))){
        		return i;
        	}
        }
        
        return 1;
    }
}
</code>

### Q4-2> PermCheck

4-1과 유사.


import java.util.HashSet;
class Solution {
    public int solution(int[] A) {
        HashSet<Integer> set = new HashSet<>();
        for(int i=0; i<A.length; i++){
        	set.add(A[i]);
        }
        for(int i=1; i<A.length+1; i++){
        	if(!set.contains(i)){
        		return 0;
        	}
        }
        return 1;
    }
}

## Algospot 
### Q> Endians
import java.util.Scanner;

public class Main {
	public static void main(String[] args) {
		Scanner scan = new Scanner(System.in);
		int i = scan.nextInt();
		while(i>0){
			Scanner scan2 = new Scanner(System.in);
			System.out.println(solution(scan2.nextInt()));
			i--;
		}
	}
	public static long solution(long A) {

		byte[] b= new byte [4];
		// & 0xff는 &연산을 함으로써 byte가 음의 값을 갖는 것을 막기 위함 
		b[0] = (byte)((A>>0)&0xff);
		b[1] = (byte)((A>>8)&0xff);
		b[2] = (byte)((A>>16)&0xff);
		b[3] = (byte)((A>>24)&0xff);
		
		long l = (long)(b[0]<<24 | b[1]<<16 | b[2]<<8 | b[3]<<0);

		return l;
    }
}
'''
