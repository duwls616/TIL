# 입력스트림과 출력스트림
> 외부로 부터 데이터를 받을때 (키보드, 파일, 네트워크상의 프로그램이 출발지가 될 수 있다.)   
데이터를 전송할땐 출력스트림 (모니터, 파일, 네트워크 상의 프로그램이 도착지가 될 수 있다.)   
단방향 통신이다.   

## java.io 패키지 
> 자바의 기본적인 데이터 입출력은 java.io 패키지에서 제공한다   
    
* File : 파일 시스템의 파일정보를 얻기 위한 클래스   
* Console : 콘솔로부터 문자를 입출력하기 위한 클래스   
* InputStream / OutputStream : 바이트 단위 입출력을 위한 최상위 입출력 스트림 클래스   
* FileInputStream/ DataOuputStream,   
ObjectInputStream / ObjectOutputStream,   
PrintStream,   
BuffetedInputStream / BufferedOutputStream : 바이트 단위 입출력을 위한 하위 스트림 클래스   
* Reader / Writer : 문자 단위 입출력을 위한 최상위 입출력 스트림 클래스   
* InputStreamReader / OutputStreamWriter,   
PrintWriter,   
BufferedReader / BufferedWriter : 문자 단위 입출력을 위한 하위 스트림 클래스   

- 바이트 단위 입출력스트림 : 그림, 멀티미디어, 문자 등 모든 종류의 데이터들을 주고 받을 수 있다.   
- 문자 단위 입출력스트림 : 문자만 주고받을 수 있다.   
    
### InputStream   
> 모든 바이트 기반 입력 스트림은 이 클래스를 상속받아서 만들어진다.	
   
* read() : 입력스트림으로부터 1바이트를 읽고 읽은 바이트를 리턴한다.   
* read(byte[] b) : 입력스트림으로부터 읽은 바이트들을 매개값으로 주어진 바이트 배열 b에 저장하고 실제로 읽은 바이트 수를 리턴한다.   
* read(byte[] b, int off, int len) : 입력 스트림으로부터 len개의 바이트만큼 읽고 매개값으로  주어진 바이트 배열 b[off]부터 len개 까지 저장한다. 실제로 읽은 바이트 수인 len개를 리턴한다. len개를 읽지못하면 실제로 읽은 바이트수를 리턴한다.   
* close() : 사용한 시스템 자원을 반납하고 입력스트림을 닫는다.   

### OutputStream 
* write(int b) : 출력 스트림으로부터 1바이트를 보낸다.(b의 끝 1바이트)   
* write(byte[] b) : 출력 스트림으로부터 주어진 바이트 배열 b의 모든 바이트를 보낸다.   
* write(byte[] b, int off, int len) : b[off]부터 len개 바이트 보낸다.   
* flush() : 버퍼에 잔류하는 모든 바이트를 출력   
* close() : 사용한 시스템 자원을 반납하고 출력 스트림 닫는다.    
   
   
외부 이미지 URL 스트림으로 받아오기   
```java
import java.io.*;
public class FileCopy1{
	public static void main(String args[] args) throws Exception{
		String path = "https://imgnews.pstatic.net/image/056/2019/11/20/0010765789_001_20191120163804442.jpg?type=w647";
		URL url = new URL(path);
		InputStream in = url.openStream();
		OutputStream out = new FileOutputStream("copy.jpg");
		
		while(true){
			int data = in.read();
			if(data == -1){
				System.out.println("end");
				break;
			}
			
			out.write(data);
		}
		in.close();
		out.close();
	}
}   
