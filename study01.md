**환경설정**

```java
package edu.medici.play369;

import edu.medici.abstractclass.AbstractPlay369;
public class Play369CharAt extends AbstractPlay369 {
	
	// 3이나 6이나 9가 있는 갯수를 체크해서 리턴해주는 테스트
	public int count(int num) {
		String nums = num + " ";  // 숫자를 문자열로 만듦
		int count = 0; // 실제 3,6,9의 개수를 저장할 변수
		for (int i = 0; i < nums.length(); i++) {
			if (nums.charAt(i) == '3' ) {
				count++;
			}else if(nums.charAt(i) == '6' ) {
				count++;
			}else if(nums.charAt(i) == '9') {
				count++;
			} 
		}
		return count;
	}
}

```


6.download
  - JDK
  - openjdk   : 무료
       https://jdk.java.net/java-se-ri/8
    [V]https://github.com/ojdkbuild/ojdkbuild
  - oralcejdk : 무료, 특정 API를 사용하면 유료
  - eclipse
  - google에서 : eclipse download 검색
