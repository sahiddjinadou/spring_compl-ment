
**Correction** :
Exercice 1 : Créer une Annotation
```java
import java.lang.annotation.ElementType;
import java.lang.annotation.Retention;
import java.lang.annotation.RetentionPolicy;
import java.lang.annotation.Target;

@Target(ElementType.METHOD)
@Retention(RetentionPolicy.RUNTIME)
public @interface Debug {
    int level() default 1;
}
```


#### Exercice 2 : Appliquer l'Annotation

```java
public class TestClass {

    @Debug(level = 3)
    public void myDebuggedMethod() {
        System.out.println("Méthode avec annotation Debug");
    }
}
```


#### Exercice 3 : Lire l'Annotation avec Réflexion
**Correction** :

```java
import java.lang.reflect.Method;

public class DebugProcessor {

    public static void main(String[] args) throws Exception {
        Method method = TestClass.class.getMethod("myDebuggedMethod");

        if (method.isAnnotationPresent(Debug.class)) {
            Debug debug = method.getAnnotation(Debug.class);
            System.out.println("Niveau de Debug : " + debug.level());
        }
    }
}
```


#### Exercice 4 : Créer une Annotation avec Plusieurs Éléments

```java
@Target(ElementType.TYPE)
@Retention(RetentionPolicy.RUNTIME)
public @interface Info {
    String author();
    String date();
}
```



#### Exercice 5 : Utiliser et Lire l'Annotation `Info`

```java
@Info(author = "John Doe", date = "2024-08-25")
public class MyClass {
    // Classe annotée
}

public class InfoReader {

    public static void main(String[] args) throws Exception {
        Info info = MyClass.class.getAnnotation(Info.class);

        if (info != null) {
            System.out.println("Auteur : " + info.author());
            System.out.println("Date : " + info.date());
        }
    }
}
```

