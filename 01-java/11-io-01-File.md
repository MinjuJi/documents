# File 클래스
- 디렉토리나 파일의 정보를 표현하는 클래스
- 파일의 내용을 포함하지 않는다.
- 실제 파일이나 디렉토리가 존재하지 않아도 File객체는 생성할 수 있다.
- 주요 생성자
  + File(String pathname)
  + File(String path, String name)
  + File(File path, String name)
- 주요 메소드
  + String getName()
    * 파일명을 반환한다.
  + long length()
    * 파일의 크기를 byte단위로 반환한다.
  + boolean exists()
    * 파일의 존재 여부를 반환한다.
  + String getAbsolutePath()
    * 파일의 전체경로를 반환한다.
  + String[] list()		
    * 디렉토리인 경우 내부의 모든 디렉토리명과 파일명을 반환한다.
  + File[] listFiles()
    * 디렉토리인 경우 내부의 모든 디렉토리와 파일에 대한 File객체들을 반환한다.
  + String getParent()
    * 부모 디렉토리명을 반환한다.
  + boolean isDirectory()
    * 디렉토리인지 여부를 반환한다.
  + boolean 	isFile()
    * 파일인지 여부를 반환한다.
  + boolean createNewFile()
    * 새로운 파일을 생성한다.
  + boolean mkdir(), mkdirs()
    * 새로운 디렉토리를 생성한다.
  + boolean delete()
    * 디렉토리나 파일을 삭제한다.
    * 디렉토리는 내부에 파일이나 디렉토리가 하나도 없어야 한다.
