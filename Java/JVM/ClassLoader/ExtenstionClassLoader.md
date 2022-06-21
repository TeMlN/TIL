## Extension ClassLoader

* `jre/lib/ext` 디렉터리나 `java.ext.dirs` 환경 변수로 지정된 폴더에 있는 클래스 파일을 로딩한다.
* 자바로 구현돼 있고 `sun.misc.Launcher` 클래스 안에 static 클래스로 구현되어 있으며, URLClassLoader를 상속하고 있다.