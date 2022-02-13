# 22-02-07 "Error: Could not find or load main class"

Support files for https://github.com/johnrengelman/shadow/issues/753 


```
> ./gradlew allJar
> java -jar build/libs/shadow-jar.jar
java -jar build/libs/shadow-jar.jar    
Error: Could not find or load main class shadow_test.Main
Caused by: java.lang.ClassNotFoundException: shadow_test.Main
```

The class is there in the JAR file:

```
> jar tvf build/libs/shadow-jar.jar| grep 'shadow_test/'
     0 Mon Feb 07 10:55:22 PST 2022 shadow_test/
  2402 Mon Feb 07 10:55:22 PST 2022 shadow_test/Main$.class
  1129 Mon Feb 07 10:55:22 PST 2022 shadow_test/Main$$anonfun$2.class
  1129 Mon Feb 07 10:55:22 PST 2022 shadow_test/Main$$anonfun$1.class
   589 Mon Feb 07 10:55:22 PST 2022 shadow_test/Main.class

```

If I unzip the jar, it is able to find the missing class and start the program

```
> cd build/libs
> unzip shadow-jar.jar
inflating: ...
...
> java -classpath . shadow_test.Main
# The program starts
```
