## Application ClassLoader
* Application ClassLoader는 classPath나 JAR파일 안에 있는 Manifest file의 Class-Path 속성값으로 지정된 폴더에 있는 클래스를 로딩한다.
* Java로 구현되어 있으며 sun.misc.Launcer 클래스 안에 static 클래스로 구현되어 있으며, URLClassLoader를 상속하고 있다.
* 우리가 직접 만들고 정의하는 클래스는 대부분 Application ClassLoader에 의해 로딩된다.