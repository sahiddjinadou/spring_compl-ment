### Module de Cours : Les Annotations en Java

#### Introduction aux Annotations

Les annotations en Java sont des métadonnées qui ajoutent des informations supplémentaires au code source. Elles sont souvent utilisées pour fournir des instructions ou des configurations aux frameworks et outils. Une annotation peut être utilisée pour marquer des classes, méthodes, champs, et autres éléments du code. Elles sont définies avec le mot-clé `@interface`.

#### 1. **Déclaration d'une Annotation**

Pour créer une annotation, utilisez le mot-clé `@interface`. Voici un exemple simple d'une annotation personnalisée :

```java
@Target(ElementType.METHOD) // L'annotation peut être appliquée aux méthodes
@Retention(RetentionPolicy.RUNTIME) // L'annotation sera disponible à l'exécution
public @interface MyCustomAnnotation {
    String value() default "default";
}
```

- **`@Target`** : Spécifie les éléments auxquels l'annotation peut être appliquée.
- **`@Retention`** : Spécifie combien de temps l'annotation doit être conservée.
- **`value()`** : Élément de l'annotation avec une valeur par défaut.

#### 2. **Utilisation d'une Annotation**

Appliquez une annotation à une méthode :

```java
public class MyClass {

    @MyCustomAnnotation(value = "important")
    public void annotatedMethod() {
        System.out.println("Méthode annotée");
    }
}
```

#### 3. **Traitement des Annotations avec Réflexion**

Pour lire et utiliser les annotations à l'exécution, utilisez la réflexion :

```java
import java.lang.reflect.Method;

public class AnnotationProcessor {

    public static void main(String[] args) throws Exception {
        Method method = MyClass.class.getMethod("annotatedMethod");

        if (method.isAnnotationPresent(MyCustomAnnotation.class)) {
            MyCustomAnnotation annotation = method.getAnnotation(MyCustomAnnotation.class);
            System.out.println("Valeur de l'annotation : " + annotation.value());
        }
    }
}
```


### Conclusion

Les annotations en Java sont puissantes pour ajouter des métadonnées et configurer des comportements de manière déclarative. Elles peuvent être traitées à l'exécution grâce à la réflexion, ce qui les rend très utiles pour les frameworks et les bibliothèques.

N'hésitez pas à expérimenter avec les annotations pour mieux comprendre leur fonctionnement et leur utilité dans vos projets Java.
