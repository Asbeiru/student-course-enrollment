# **Student-Course-Enrollment**

## **项目简介**

`Student-Course-Enrollment` 是一个基于 **Spring Boot** 和 **Spring Data JPA** 的示例项目，旨在帮助开发者学习和实践 JPA 的核心功能。  
本项目模拟了一个大学管理系统的核心功能，包括学生管理、课程管理，以及学生与课程之间的注册关系管理。通过实现常见的数据库关系（1对1、1对多、多对多），你将深入理解 Spring Data JPA 的使用方法。

### **核心功能**

1. 学生管理：支持添加、更新、删除和查询学生信息。
2. 课程管理：支持添加、更新、删除和查询课程。
3. 学生课程注册：学生可以注册多个课程，课程也可以有多个学生。
4. 数据模型扩展：包括学生与身份证的 **1 对 1** 关系、学生与书籍的 **1 对多** 关系。

---

## **功能列表**

1. **学生管理**
    - 添加新学生
    - 更新学生信息
    - 删除学生
    - 查询所有学生

2. **课程管理**
    - 添加新课程
    - 更新课程信息
    - 删除课程
    - 查询所有课程

3. **注册管理**
    - 学生可以注册多个课程
    - 查看学生的注册课程列表
    - 删除学生的某门课程

4. **其他功能**
    - 学生与身份证的 1 对 1 关系
    - 学生与书籍借阅的 1 对多关系
    - 数据库查询和动态查询

---

## **技术栈**

本项目使用以下技术和工具：

- **后端**
    - Spring Boot
    - Spring Data JPA
    - Hibernate
    - H2 Database（默认内存数据库，可替换为 MySQL/PostgreSQL）
    - Lombok（简化 Java 代码）

- **构建工具**
    - Maven 或 Gradle

- **测试**
    - JUnit 5
    - Spring Boot Test

---

## **安装和运行**

### **1. 克隆仓库**

使用以下命令克隆项目到本地：

```bash
git clone https://github.com/your-username/student-course-enrollment.git
cd student-course-enrollment
```

### **2. 配置环境**

本项目默认使用 H2 内存数据库，无需额外配置。如需切换到 MySQL 或其他数据库，请修改 `src/main/resources/application.yml` 文件。

### **3. 启动项目**

使用以下命令启动项目：

```bash
# 如果使用 Maven
mvn spring-boot:run

# 如果使用 Gradle
./gradlew bootRun
```

项目启动后，默认接口地址为：`http://localhost:8080/api`。

### **4. 访问 H2 控制台**

H2 数据库控制台地址：`http://localhost:8080/h2-console`  
默认配置如下：
- **JDBC URL**: `jdbc:h2:mem:testdb`
- **用户名**: `sa`
- **密码**: `(空)`

---

## **数据模型设计**

本项目包含以下核心实体及关系：

1. **学生 (Student)**
    - ID（主键）
    - 姓名、邮箱、年龄

2. **课程 (Course)**
    - ID（主键）
    - 课程名称

3. **注册 (Enrollment)**
    - 学生与课程的多对多关系

4. **身份证 (StudentIdCard)**
    - 与学生的一对一关系

5. **图书 (Book)**
    - 与学生的一对多关系

### **数据关系图**

```plaintext
1 对 1：Student ↔ StudentIdCard
1 对 多：Student ↔ Book
多 对 多：Student ↔ Enrollment ↔ Course
```

---

## **API 文档**

### **学生管理 API**

| 方法  | URL                  | 描述                |
|-------|----------------------|---------------------|
| GET   | `/api/students`      | 查询所有学生        |
| GET   | `/api/students/{id}` | 按 ID 查询学生      |
| POST  | `/api/students`      | 添加新学生          |
| PUT   | `/api/students/{id}` | 更新学生信息        |
| DELETE| `/api/students/{id}` | 删除学生            |

### **课程管理 API**

| 方法  | URL                  | 描述                |
|-------|----------------------|---------------------|
| GET   | `/api/courses`       | 查询所有课程        |
| POST  | `/api/courses`       | 添加新课程          |
| DELETE| `/api/courses/{id}`  | 删除课程            |

### **注册管理 API**

| 方法  | URL                              | 描述                     |
|-------|----------------------------------|--------------------------|
| POST  | `/api/students/{id}/enroll`      | 为学生注册课程           |
| DELETE| `/api/students/{id}/courses/{id}`| 删除学生的某门课程       |

---

## **测试与扩展**

### **测试覆盖范围**

- 学生管理功能
- 课程注册功能
- 数据库关系的正确性
- API 的单元测试和集成测试

### **扩展建议**

1. 添加更多领域模型，如教师 (Teacher)、班级 (Class) 等。
2. 实现课程的时间表管理功能。
3. 添加分页和排序功能。
4. 使用 Docker 容器化项目。
5. 在前端开发一个简单的 UI 界面配合使用。

---

## **许可证**

本项目采用 [MIT License](https://opensource.org/licenses/MIT) 开源，欢迎使用与贡献。

---

## **项目作者**

作者：_你的名字_  
GitHub：[your-username](https://github.com/your-username)

---

希望这个 README 文件清晰且全面，可以满足你项目的需求！如果有需要进一步调整或补充的地方，随时可以修改！ 😊