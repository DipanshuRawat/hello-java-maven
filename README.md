# 📚 Task 8: Run a Simple Java Maven Build Job in Jenkins

## 🌟 Objective:
how to use **Jenkins** to build a simple Java application using **Maven** 
---

## 🛠 Tools Required (All Free):
- Jenkins (installed locally or via Docker)
- Java JDK 8 or 11
- Maven

---

## 🛆 Deliverables:
- A basic Java HelloWorld app (with `pom.xml`)
- Jenkins **Freestyle Job** configured to build it
- Screenshot of successful **build console output**

---

## 📂 Sample Dataset/Repo Structure:
Repository Name: **hello-java-maven**

```
hello-java-maven/
├── pom.xml
└── src/
    └── main/
        └── java/
            └── HelloWorld.java
```

---

## 🧹 Application Code:

**HelloWorld.java**
```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, Jenkins + Maven!");
    }
}
```

**pom.xml**
```xml
<project>
    <modelVersion>4.0.0</modelVersion>
    
    <groupId>com.example</groupId>
    <artifactId>hello</artifactId>
    <version>1.0</version>

    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.8.1</version>
                <configuration>
                    <source>1.8</source>
                    <target>1.8</target>
                </configuration>
            </plugin>
        </plugins>
    </build>
</project>
```

---

## 🧽 Step-by-Step Guide:

### 1. Create the Java Application:
- Create the project folder structure as shown above.
- Add the `HelloWorld.java` inside `src/main/java/`.
- Add the `pom.xml` at the root.

---

### 2. Start Jenkins:
If using Docker:
```bash
docker run -p 8080:8080 jenkins/jenkins:lts
```

---

### 3. Configure Jenkins:

1. Go to **Manage Jenkins → Global Tool Configuration**:
    - **Add JDK** (Java 8 or 11)

![image](https://github.com/user-attachments/assets/254e9ebb-aa13-4702-a8d2-17c6f9b53e98)

    - **Add Maven** (e.g., Maven 3.8.6)

![image](https://github.com/user-attachments/assets/86709904-e4b6-4613-931b-136e4995c8a8)


2. Make sure both Java and Maven paths are correctly set.

---

### 4. Create a Jenkins Freestyle Project:

- Create a **new Freestyle project** (e.g., `hello-java-maven`).
  
![image](https://github.com/user-attachments/assets/5369eb12-2d85-497b-a59b-73c26fa73e8a)

- In **Source Code Management**, select:
  - None (or Git if you have a repo).
- In **Build Environment**, leave default.
- In **Build Section**:
  - Choose **"Invoke top-level Maven targets"**.
  - Set **Goals** to:
    ```
    clean package
    ```

- (Optional) Add a **Post-build Step** (Execute Shell) to run the jar:
    ```bash
    java -cp target/hello-1.0.jar HelloWorld
    ```

---

### 5. Build the Job:
- Click **"Build Now"**.
- Check the **Console Output**.
- 
![image](https://github.com/user-attachments/assets/61c48f1c-261f-49a9-8716-29558ef1fe09)

![image](https://github.com/user-attachments/assets/883403ba-3f6a-44a2-9a28-818b3a7b1b90)

---

### 6. Expected Output:
👌 You should see:

```
Hello, Jenkins + Maven!
```
and
```
BUILD SUCCESS
```

---

# 🏁 Done!
