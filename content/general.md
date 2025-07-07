# General
General programming concepts, design patterns

* [What is delegation?](#What-is-delegation)
* [How delegation works?](#How-delegation-works)
* [What are benefits of delegation?](#What-are-benefits-of-delegation)
* [What are SOLID principles?](#What-are-SOLID-principles)
* [What is dependency injection?](#What-is-dependency-injection)
* [Types of dependency injection](#Types-of-dependency-injection)
* [Benefits of dependency injection](#Benefits-of-dependency-injection)
* [Dependency Injection in Swift](#Dependency-Injection-in-Swift)
* [What is MVVM?](#What-is-MVVM)
* [Components of MVVM: Model](#Components-of-MVVM-Model)
* [Components of MVVM: View](#Components-of-MVVM-View)
* [Components of MVVM: ViewModel](#Components-of-MVVM-ViewModel)
* [How MVVM works together](#How-MVVM-works-together)
* [MVVM example flow](#MVVM-example-flow)
* [Benefits of MVVM](#Benefits-of-MVVM)
* [What are top 5 interview data structures?](#What-are-top-5-interview-data-structures)
* [What are top 5 interview algorithms?](#What-are-top-5-interview-algorithms)
* [What is Gerrit?](#What-is-Gerrit)
* [What are most popular CI/CD tools?](#What-are-most-popular-CI-CD-tools)
* [What is Docker?](#What-is-Docker)
* [What is Apache Spark?](#What-is-Apache-Spark)
* [What is Apache Kafka?](#What-is-Apache-Kafka)
* [What is Terraform?](#What-is-Terraform)
* [What is GraphQL?](#What-is-GraphQL)
* [Best practices for dependencies versioning in own libraries](#Best-practices-for-dependencies-versioning-in-own-libraries)

## What is delegation?
Delegation is a design pattern in many programming languages that allows one object to hand off (or delegate) responsibility for a specific task to another object. This pattern is commonly used to customize or alter the behavior of objects in a decoupled and reusable way.

### Key concepts of delegation
- **Delegate**: The object that receives the responsibility to perform a task. It typically conforms to a protocol that defines the methods or properties it must implement.

- **Delegating object**: The object that delegates the responsibility for certain tasks to the delegate. It typically holds a reference to the delegate and calls methods on the delegate at appropriate times.

- **Protocol**: A protocol is used to define the methods and properties that the delegate must implement. This ensures that the delegate has the required methods for handling the delegated tasks.

## How delegation works?
1. **Define a protocol**: Create a protocol that defines the responsibilities or tasks that need to be delegated. The delegate object will conform to this protocol.

2. **Create a delegate property**: In the delegating object, create a property that holds a reference to the delegate. This property is typically declared as optional to allow the delegating object to work even if no delegate is assigned.

3. **Implement protocol methods**: The delegate object conforms to the protocol and implements the required methods to handle the delegated tasks.

4. **Delegate the tasks**: The delegating object calls the delegate's methods when needed, passing the responsibility to the delegate.

## What are benefits of delegation?
- **Separation of concerns**: Delegation allows you to separate responsibilities between different objects, making your code more modular and easier to manage.

- **Reusability**: The delegating object can be reused with different delegate objects, each providing different behavior.

- **Customizability**: The delegate can customize the behavior of the delegating object without subclassing or modifying its code.

## What are SOLID principles?
- **Single-responsibility**: There should never be more than one reason for a class to change. In other words, every class should have only one responsibility.

- **Open–closed**: Software entities should be open for extension but closed for modification.

- **Liskov substitution**: Functions that use pointers or references to base classes must be able to use objects of derived classes without knowing it.

- **Interface segregation**: Clients should not be forced to depend upon interfaces that they do not use.

- **Dependency inversion**: Depend upon abstractions, not concretes.

## What is dependency injection?
Dependency injection (DI) is a design pattern used in software development to achieve Inversion of Control (IoC) between a class and its dependencies. In simpler terms, dependency injection allows an object to receive its dependencies from an external source rather than creating them itself. This pattern promotes loose coupling between components, making the code more modular, testable, and easier to maintain.

### Key concepts of dependency injection
- **Dependency**: A dependency is any object or service that a class needs to function. For example, if a class `Car` needs an `Engine` object to operate, `Engine` is a dependency of `Car`.

- **Injection**: Injection refers to the process of providing dependencies to a class. The class doesn't create the dependencies; instead, they are passed to it from the outside.

- **Inversion of Control (IoC)**: IoC is a principle where the control of creating and managing dependencies is inverted from the class to an external source. Dependency injection is one way to achieve IoC.

## Types of dependency injection
There are several ways to inject dependencies into a class:

- **Constructor injection**: Dependencies are provided through the class constructor.
```swift
class Engine {
    // Engine properties and methods
}

class Car {
    let engine: Engine

    init(engine: Engine) {
        self.engine = engine
    }
}

let engine = Engine()
let car = Car(engine: engine)  // Injecting the dependency
```
- **Property injection**: Dependencies are set via properties after the object is created.
```swift
class Car {
    var engine: Engine?

    func setEngine(_ engine: Engine) {
        self.engine = engine
    }
}

let car = Car()
car.setEngine(Engine())  // Injecting the dependency via a property
```
- **Method injection**: Dependencies are provided as parameters to a method.
```swift
class Car {
    func drive(with engine: Engine) {
        // Use the engine
    }
}

let car = Car()
car.drive(with: Engine())  // Injecting the dependency via a method
```
- **Interface injection** (less common in Swift): Dependencies are injected via an interface (or protocol in Swift), requiring the class to implement the interface that sets the dependency.
```swift
protocol EngineInjectable {
    func setEngine(_ engine: Engine)
}

class Car: EngineInjectable {
    var engine: Engine?

    func setEngine(_ engine: Engine) {
        self.engine = engine
    }
}
```

## Benefits of dependency injection
- **Loose coupling**: Classes are less dependent on specific implementations of their dependencies, making them easier to change or 
replace.

- **Testability**: You can easily replace real dependencies with mock objects, making unit testing easier.

- **Reusability**: Since classes do not depend on specific implementations, they can be reused in different contexts with different dependencies.

- **Flexibility**: Dependencies can be configured externally, making it easier to manage complex dependencies and configurations.

## Dependency Injection in Swift
In Swift, dependency injection is commonly used in scenarios like:
- **Network requests**: Injecting different network clients or mock clients.
- **View controllers**: Injecting view models or services into view controllers.
- **Testing**: Replacing real services with mock services to test specific behaviors.

Example in a Swift-based iOS app:
```swift
class NetworkService {
    func fetchData() {
        // Network fetching logic
    }
}

class ViewModel {
    private let networkService: NetworkService

    init(networkService: NetworkService) {
        self.networkService = networkService
    }

    func loadData() {
        networkService.fetchData()
    }
}

let networkService = NetworkService()
let viewModel = ViewModel(networkService: networkService)
```
In this example:
- `NetworkService` is a dependency of `ViewModel`.
- The `ViewModel` doesn't create the `NetworkService` itself. Instead, it receives it from the outside, which is dependency injection.

## What is MVVM?
MVVM (Model-View-ViewModel) is a design pattern used in software development, particularly in the context of building user interfaces. It’s a way of organizing code that separates concerns, making it easier to manage, maintain, and test an application's codebase. MVVM is especially popular in frameworks like SwiftUI, WPF (Windows Presentation Foundation), and others that emphasize data binding.

### Components of MVVM
- **Model**

- **View**

- **ViewModel**

MVVM is a powerful design pattern that helps structure your code in a way that makes it more maintainable, testable, and scalable. By separating the concerns of data management, business logic, and UI, MVVM allows developers to focus on different aspects of the application independently, leading to cleaner and more efficient codebases. SwiftUI's declarative nature and support for data binding make it a natural fit for implementing the MVVM pattern.

## Components of MVVM: Model
- The `Model` represents the data and business logic of the application. It includes the data structures, network requests, database management, and any rules or logic that pertain to the data.

- In simple terms, the `Model` defines the structure of the data your application works with and the operations you can perform on that data.

Example:
```swift
struct User {
    let id: Int
    let name: String
}
```

## Components of MVVM: View
- The `View` is the user interface of the application. It displays the data provided by the `ViewModel` and handles user interactions like taps and gestures.

- The `View` should be as simple as possible, focusing on presentation and delegating all logic to the `ViewModel`.

Example:
```swift
struct UserView: View {
    @ObservedObject var viewModel: UserViewModel

    var body: some View {
        VStack {
            Text(viewModel.userName)
            Button(action: {
                viewModel.loadUserData()
            }) {
                Text("Load User Data")
            }
        }
    }
}
```

## Components of MVVM: ViewModel
- The `ViewModel` serves as an intermediary between the `Model` and the `View`. It holds the logic for transforming the data from the `Model` into a format that the `View` can easily display.

- The `ViewModel` also handles user input and updates the `Model` or performs actions accordingly.

- It exposes the data to the `View` using observable properties or bindings so that the `View` can automatically update when the data changes.

Example:
```swift
class UserViewModel: ObservableObject {
    @Published var userName: String = ""
    private let userService: UserService

    init(userService: UserService) {
        self.userService = userService
    }

    func loadUserData() {
        let user = userService.getUser()
        userName = user.name
    }
}
```

## How MVVM works together
- **Model**: The `Model` layer doesn't know anything about the `View` or `ViewModel`. It's pure data and business logic.

- **ViewModel**: The `ViewModel` interacts with the `Model` to retrieve or manipulate data. It doesn't directly interact with the `View` but instead exposes data through properties that the `View` observes.

- **View**: The `View` observes the `ViewModel` for any changes. When the `ViewModel` updates its properties, the `View` automatically updates the UI to reflect these changes. The `View` also sends user interactions (like button taps) to the `ViewModel`.

## MVVM example flow
- **Data fetching**: A user presses a "Load Data" button in the `View`. This action is passed to the `ViewModel`.

- **Data processing**: The `ViewModel` then asks the `Model` to fetch the data. The `Model` might perform a network request or access a database.

- **Data update**: Once the `Model` returns the data, the `ViewModel` processes it (if necessary) and updates its observable properties.

- **UI update**: The `View` observes the changes in the `ViewModel`'s properties and updates the user interface accordingly.

## Benefits of MVVM
- **Separation of concerns**: By separating the UI (View) from the business logic (ViewModel) and data (Model), you make the code more modular and easier to manage.

- **Testability**: The `ViewModel` is independent of the `View`, making it easier to test. You can write unit tests for the `ViewModel` without needing to test the UI.

- **Reusability**: Since the `ViewModel` is independent of any specific UI, it can be reused across different views or platforms.

- **Data binding**: Especially in frameworks like SwiftUI, data binding allows the `View` to automatically update when the `ViewModel` changes, reducing boilerplate code.

## What are top 5 interview data structures?
## 1. Stack
## 2. Heap
## 3. Graphs
## 4. Binary tree
## 5. Hash map / set

## What are top 5 interview algorithms?
## 1. Top k elements
## 2. Dynamic programming
## 3. Backtracking
## 4. Sliding window
## 5. Breadth first search and depth first search

## What is Gerrit?
Gerrit is a web-based code review tool that integrates with Git to facilitate collaborative software development. It allows teams to review, discuss, and approve code changes before they are merged into a codebase. Gerrit provides a structured workflow where contributors submit changes (also known as patch sets) for review, and other team members can inspect, comment on, and suggest modifications to the code. It supports features like:

- **Version control integration**: Gerrit works directly with Git, one of the most popular version control systems. Every change is stored in Git as a commit, and the review process is tightly coupled with Git workflows.

- **Access control**: Gerrit has detailed permissions, allowing admins to control who can submit, review, and approve changes.

- **Change approval**: It requires changes to be reviewed and explicitly approved before they can be merged.

- **Automated testing**: Gerrit can integrate with Continuous Integration (CI) tools to run tests automatically on submitted changes.

The primary goal of Gerrit is to improve the quality of the code through peer review, helping to catch bugs, enforce coding standards, and ensure that only high-quality code is integrated into the main project.

## What are most popular CI/CD tools?
There are several popular Continuous Integration (CI) and Continuous Deployment/Delivery (CD) tools that developers and organizations commonly use to automate testing, building, and deployment of code. Some of the most popular CI/CD tools include:

1. **Jenkins**
- Type: Open-source
- Overview: One of the most widely-used CI/CD tools. Jenkins is highly customizable and supports a vast array of plugins for various build, deployment, and automation needs.
- Key features:
  - Pipeline as code (using Jenkinsfile)
  - Extensible through plugins
  - Integrates with most popular tools in the DevOps ecosystem
  - Active open-source community

2. **GitLab CI/CD**
- Type: Integrated with GitLab (open-source and SaaS versions)
- Overview: GitLab CI/CD is tightly integrated with GitLab's version control and offers built-in tools for managing the entire DevOps lifecycle, from development to deployment.
- Key features:
  - Pipeline definitions using .gitlab-ci.yml
  - Auto DevOps for CI/CD best practices
  - Seamless integration with GitLab repositories
  - Container registry and Kubernetes support

3. **CircleCI**
- Type: SaaS
- Overview: A popular cloud-based CI/CD platform known for its speed and ease of use. CircleCI provides flexibility in defining workflows and integrates well with GitHub, Bitbucket, and other repositories.
- Key Features:
  - Quick setup for both cloud and self-hosted versions
  - Native Docker support
  - Workflow and parallelism for faster build times
  - Comprehensive configuration with YAML

4. **Travis CI**
- Type: SaaS (with limited free options for open-source projects)
- Overview: One of the earliest hosted CI/CD tools, widely used by open-source projects on GitHub. Travis CI is easy to configure and well-integrated with GitHub.
- Key features:
  - Simple configuration using .travis.yml
  - Integrates with various cloud services
  - Automated deployment support to multiple platforms (Heroku, AWS, etc.)
  - Good for open-source projects with free plans

5. **Azure Pipelines**
- Type: Part of Azure DevOps (SaaS)
- Overview: A powerful CI/CD service from Microsoft that supports multi-platform builds, including macOS, Linux, and Windows. It’s flexible and can integrate with GitHub and Azure Repos.
- Key features:
  - YAML-based pipeline definition
  - Cloud-hosted build agents
  - Integration with Azure services and Kubernetes
  - Free tier for open-source projects

6. **GitHub Actions**
- Type: SaaS (GitHub-native)
- Overview: GitHub Actions is GitHub's built-in automation platform that enables developers to automate workflows directly within their GitHub repositories. It has become increasingly popular because of its deep integration with GitHub repositories.
- Key Features:
  - Native GitHub integration
  - Supports YAML for workflow definitions
  - Large marketplace for reusable actions
  - Matrix builds and concurrent jobs

7. **Bamboo**
- Type: Proprietary (by Atlassian)
- Overview: A CI/CD tool developed by Atlassian, Bamboo integrates well with other Atlassian tools like Jira and Bitbucket, offering an end-to-end solution for automated builds, tests, and releases.
- Key features:
  - Native integration with Atlassian tools
  - Configurable pipelines with different triggers
  - Supports Docker, AWS, and Kubernetes

8. **TeamCity**
- Type: Proprietary (by JetBrains)
- Overview: A powerful and flexible CI/CD tool that supports a variety of development ecosystems and languages. TeamCity offers deep integration with JetBrains products like IntelliJ IDEA.
- Key features:
  - Extensive language and platform support
  - Configurable build pipelines
  - Build history tracking
  - Parallel builds and out-of-the-box scalability

9. **Bitbucket Pipelines**
- Type: SaaS (integrated with Bitbucket)
- Overview: Bitbucket Pipelines is Atlassian's native CI/CD tool for Bitbucket repositories, offering an easy way to set up CI/CD pipelines within the Bitbucket environment.
- Key features:
  - YAML-based configuration
  - Tight Bitbucket integration
  - Simple setup for builds, tests, and deployments
  - Docker-based pipeline execution

10. **AWS CodePipeline**
- Type: Proprietary (Amazon Web Services)
- Overview: A fully managed CI/CD service that automates the build, test, and deploy process for AWS applications. It's ideal for teams already using the AWS ecosystem.
- Key features:
  - Deep integration with AWS services (e.g., S3, ECS, Lambda)
  - Automated deployments to AWS environments
  - Easy setup for pipelines using CodeBuild, CodeDeploy, and other AWS tools

These tools offer a wide range of capabilities, from simple CI/CD pipelines to more complex DevOps workflows, and are widely adopted across various industries and development environments.

## What is Docker?
Docker is an open-source platform that allows developers to automate the deployment, scaling, and management of applications by packaging them in containers. Containers are lightweight, standalone, and executable software packages that include everything needed to run an application: code, libraries, dependencies, and the runtime environment.

### Key features of Docker:
1. **Containerization**: Docker containers isolate applications from the underlying system, ensuring that they run consistently across different environments (development, testing, production).

2. **Portability**: Once an application is containerized, it can run on any machine that supports Docker, regardless of underlying infrastructure.

3. **Efficiency**: Containers share the host system's kernel, which makes them more lightweight compared to virtual machines (VMs) that require their own operating system.

4. **Scalability**: Docker works seamlessly with orchestration tools like Kubernetes, making it easier to scale applications across multiple containers.

5. **Version control**: Docker images, which are used to create containers, can be versioned, making it easy to roll back to previous versions of an application if needed.

### Components of Docker:
- **Docker engine**: The core technology that enables containerization.

- **Docker images**: Templates used to create containers. They are read-only and contain the application code along with its dependencies.

- **Docker containers**: Running instances of Docker images.

- **Docker hub**: A cloud-based repository for sharing and storing Docker images.

Docker is widely used in DevOps, microservices architecture, and cloud-based applications due to its flexibility and ability to standardize environments.

## What is Apache Spark?
Apache Spark is an open-source distributed computing system designed for big data processing and analytics. It was developed at UC Berkeley’s AMPLab in 2009 and has since become one of the most popular tools for large-scale data processing. Spark is known for its speed, ease of use, and advanced analytics capabilities such as machine learning and graph processing.

### Key features of Apache Spark:
1. **In-Memory processing**: Spark processes data in memory (RAM), making it much faster than traditional disk-based processing systems like Hadoop MapReduce. This allows for significantly faster data retrieval and processing.

2. **Unified engine**: It provides a single, integrated platform to handle multiple types of data workloads, including:

- **Batch processing**: Processing large datasets in chunks.
- **Real-time stream processing:** Handling data streams in real-time using Spark Streaming.
- **Interactive queries**: Allowing users to interact with their data through tools like Apache Zeppelin or Jupyter notebooks.
- **Graph processing**: Using the GraphX API for graph analytics.
- **Machine learning**: Leveraging the MLlib library for machine learning algorithms.

3. **Scalability**: Spark can scale from running on a single machine to thousands of machines, making it suitable for massive datasets and complex data workflows.

4. **Compatibility**: Spark can integrate with many storage systems such as Hadoop’s HDFS, Amazon S3, Cassandra, and Apache HBase, allowing it to handle a wide variety of data sources.

5. **Rich API**: It supports APIs in multiple programming languages including Python, Java, Scala, and R, which makes it accessible to a broad range of developers.

### Common use cases:
- **Data analysis and reporting: Spark is often used for big data analytics, enabling businesses to gain insights from their data quickly.

- **Real-time data processing**: Applications like monitoring systems, IoT devices, and log analytics rely on Spark’s real-time processing capabilities.

- **Machine learning**: Its MLlib library provides out-of-the-box machine learning algorithms such as classification, regression, and clustering.

- **ETL pipelines**: Spark is commonly used for Extract, Transform, and Load (ETL) jobs, where it processes large datasets to extract useful information and load it into data warehouses or databases.

In summary, Apache Spark is a powerful tool for big data processing that excels in performance and flexibility, making it a go-to choice for organizations dealing with large-scale data challenges.

## What is Apache Kafka?
Apache Kafka is an open-source, distributed event streaming platform primarily used for building real-time data pipelines and streaming applications. Developed by LinkedIn and later open-sourced, Kafka is designed to handle high throughput, fault tolerance, and scalability, making it a popular choice for real-time data processing.

### Key features of Apache Kafka:
1. **High throughput and low latency**: Kafka is capable of handling millions of events per second with very low latency. It is optimized for both high write and read throughput, making it suitable for high-performance, real-time data pipelines.

2. **Distributed architecture**: Kafka is built to scale horizontally by distributing data across multiple machines (brokers). This ensures fault tolerance and allows Kafka to handle large volumes of data efficiently.

3. **Pub-sub messaging model**:

- **Producers**: Producers publish data (events or messages) to Kafka topics.
- **Consumers**: Consumers read data from these topics.
- This model allows multiple consumers to read the same data independently, which is crucial for data pipelines where the same event needs to be processed by different systems.

4. **Durability and fault tolerance**: Kafka stores data durably on disk, and data is replicated across multiple brokers in a Kafka cluster to ensure high availability and fault tolerance. Even if a broker fails, data is not lost.

5. **Log-based storage**: Kafka operates as a distributed commit log. All events are stored in a partitioned log structure, and consumers can replay or reread data at any time, making it useful for applications that need historical data.

6. **Scalability**: Kafka is designed to scale easily. Topics in Kafka can be partitioned, allowing data to be split and distributed across multiple brokers. Each partition can be consumed independently, which allows Kafka to scale horizontally across a large number of consumers.

7. **Real-time stream processing: Kafka works well with stream processing frameworks like Apache Spark and Apache Flink, and it has its own stream processing library, Kafka Streams, for building real-time processing applications.

8. **Decoupling systems**: Kafka allows systems to produce and consume data asynchronously, meaning the producers and consumers don’t need to interact with each other directly. This enables easy decoupling of services in a microservices architecture.

### Common use cases:
- **Real-time analytics**: Kafka is widely used for collecting and processing real-time data streams, such as log aggregation, clickstream analysis, and monitoring data.

- **Event sourcing**: Kafka is often used for event-driven architectures where changes in the system are represented as streams of events.

- **Data integration and ETL**: Kafka can be used to integrate data across multiple systems, often as a backbone for real-time data pipelines, handling ETL (Extract, Transform, Load) processes in real-time.

- **Messaging system**: Kafka serves as a high-throughput message broker for applications that need to process data asynchronously.

- **Log aggregation**: Kafka can act as a centralized hub for aggregating logs from different services, making it easier to manage and analyze.

### Components of Kafka:
- **Brokers**: Kafka clusters are made up of one or more brokers. Each broker is responsible for storing and serving partitions of topics.

- **Topics**: Data in Kafka is categorized into topics. Each topic is split into partitions for scalability.

- **Producers**: Producers publish (or send) messages to Kafka topics.

- **Consumers**: Consumers read messages from Kafka topics.

- **Zookeeper**: Until recently, Kafka used Apache Zookeeper to manage the cluster's metadata and maintain configuration consistency across brokers. Newer versions of Kafka are moving toward a Zookeeper-free architecture.

In summary, Apache Kafka is a powerful, scalable, and fault-tolerant platform designed to handle large volumes of streaming data, making it an essential tool in many modern data infrastructures.

## What is Terraform?
Terraform is an open-source **infrastructure as code (IaC)** tool created by HashiCorp. It allows users to define, provision, and manage cloud infrastructure in a declarative configuration language called **HashiCorp Configuration Language (HCL)** or JSON. Terraform can manage infrastructure across a wide range of platforms, including public clouds (like AWS, Azure, and Google Cloud), private clouds, and on-premises environments.

### Key features of Terraform:
- **Infrastructure as Code (IaC)**:
Terraform allows users to define infrastructure using code, enabling version control, collaboration, and reuse. Instead of manually creating or configuring resources through cloud provider interfaces, you can write code that describes the desired infrastructure, and Terraform will create and manage it.

- **Declarative language**:
Terraform uses a declarative approach, meaning you specify what infrastructure you want, rather than providing step-by-step instructions for how to create it. Terraform then determines how to achieve the desired state.

- **Multi-cloud support**:
Terraform can manage infrastructure across different cloud providers and services (such as AWS, Azure, Google Cloud, VMware, and others) using providers. This makes it possible to manage hybrid or multi-cloud architectures with a unified tool.

- **State management**:
Terraform keeps track of the current state of your infrastructure in a state file. This allows it to understand which resources have already been provisioned and which are new or need updates. By comparing the actual state of your infrastructure with the desired state (as defined in the configuration), Terraform can determine the necessary changes.

- **Plan and apply**:
  - Terraform Plan: Before applying changes, Terraform generates an execution plan, showing exactly what changes it will make to your infrastructure. This ensures you can preview changes and avoid potential misconfigurations.
  - Terraform Apply: Once reviewed, the changes are applied to create, update, or delete resources as necessary.

- **Modularity and reusability**:
Terraform encourages the use of modules to break down your infrastructure into smaller, reusable components. This modularity promotes efficiency and allows teams to share, version, and reuse common infrastructure patterns across projects.

- **Immutable Infrastructure**:
Terraform helps enforce the concept of immutable infrastructure, where instead of modifying running resources, changes are applied by creating new infrastructure and then replacing the old one. This makes it easier to maintain stability and predictability.

- **Provisioners and plugins**:
  - Terraform can also use provisioners to execute scripts or commands on resources, though it’s generally preferred to manage software configuration through other tools like Ansible, Chef, or Puppet.
  - Providers are plugins that enable Terraform to interact with various services and platforms. Providers allow Terraform to provision and manage infrastructure across different services (e.g., AWS, Azure, Kubernetes).

- **Collaboration with remote backends**:
Terraform allows you to store your state file remotely using backends like Amazon S3, Google Cloud Storage, or Terraform Cloud. This supports collaboration across teams by ensuring that everyone is working with a single, consistent state.

### Common use cases:
- **Infrastructure provisioning**: Automating the provisioning of cloud resources such as VMs, networks, databases, and other services.

- **Multi-cloud management**: Managing resources across different cloud platforms in a consistent and automated way.

- **Versioned infrastructure**: Using version control to manage infrastructure changes, enabling rollback and tracking of changes over time.

- **Hybrid cloud and on-premise**: Managing both cloud and on-premise infrastructure from a single tool.

- **Disaster recovery**: Using Terraform to quickly rebuild infrastructure in the event of a failure by applying the configuration in a new region or data center.

### Example workflow:
- **Write configuration**: Define your desired infrastructure using HCL (HashiCorp Configuration Language).
```
provider "aws" {
  region = "us-west-2"
}

resource "aws_instance" "example" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"
}
```

- **Initialize terraform**: Run terraform init to download necessary plugins/providers.

- **Create an execution plan**: Run terraform plan to preview what Terraform will do.
- **Apply changes**: Run terraform apply to create or update the infrastructure.
- **Manage infrastructure**: As your needs evolve, modify the configuration and use Terraform to keep your infrastructure in sync with the desired state.

### Benefits of terraform:
- **Automation**: Terraform automates infrastructure creation, reducing the risk of human error.

- **Consistency**: Using code to define infrastructure ensures that environments are created and managed in a consistent way.

- **Collaboration**: Terraform makes it easier for teams to collaborate on infrastructure, using version control for the infrastructure definitions.

- **Scalability**: It simplifies the process of scaling infrastructure, both horizontally and across different cloud providers.

In summary, Terraform is a highly flexible and scalable tool that automates the provisioning, management, and orchestration of infrastructure across multiple platforms, using a declarative approach to define and track infrastructure.

## What is GraphQL?
GraphQL is a query language for APIs, and a runtime for executing those queries by allowing clients to request only the data they need. It was developed by Facebook in 2012 and released publicly in 2015. GraphQL provides a more flexible and efficient alternative to traditional REST APIs by enabling clients to request specific fields of data from a server, rather than receiving entire data objects or endpoints, which often return excess data.

### Key features of GraphQL:
- **Single endpoint**: Unlike REST, where multiple endpoints are often needed for different resources, GraphQL uses a single endpoint to handle all queries and mutations (changes to data).

- **Flexible queries**: Clients can specify exactly what data they want in the query, allowing for more efficient data retrieval. For example, a client can request just a user’s name and email without fetching other details like address or age.

- **Strong typing**: GraphQL schemas define the shape of the data, types, and relationships, which ensures that queries are well-defined and consistent.

- **Real-time updates (subscriptions)**: GraphQL supports subscriptions, allowing clients to receive real-time data updates from the server whenever a certain event occurs.

- **No over-fetching or under-fetching**: By specifying only the needed fields, GraphQL avoids the problems of over-fetching (getting too much unnecessary data) or under-fetching (requiring multiple requests to get all needed data), common with REST APIs.

### Example
Here is a simple GraphQL query requesting a user's name and email:

```graphql
{
  user(id: "1") {
    name
    email
  }
}
```
In response, the server would only return:
```json
{
  "data": {
    "user": {
      "name": "John Doe",
      "email": "john.doe@example.com"
    }
  }
}
```

### Benefits
- **Efficiency**: Clients can ask for exactly what they need, reducing data transfer over networks.
- **Self-descriptive**: Clients can inspect the API's schema and know what data can be requested, leading to easier development and integration.
- **Version-less API**: Since clients dictate the structure of the response, GraphQL APIs often don’t require versioning like REST APIs.

### Drawbacks
- **Complexity**: GraphQL can be more complex to implement on the server side, especially when dealing with performance optimization for large datasets.
- **Overhead**: Complex queries might lead to increased processing time on the server.

It's often compared to REST, but GraphQL tends to be preferred in applications where data needs vary greatly or where minimizing data load and increasing flexibility are key concerns.

Apollo iOS SDK

## Best practices for dependencies versioning in own libraries
When managing versioning for your own libraries (whether they're internal to your organization or open-source), it's important to ensure that your library is easy to adopt, update, and maintain for its consumers. Proper versioning plays a critical role in communicating changes and ensuring backward compatibility. Here are the best practices for versioning your own libraries:

1. Follow semantic versioning strictly
- Semantic Versioning (SemVer) ensures that consumers of your library understand what to expect when upgrading versions. SemVer uses a MAJOR.MINOR.PATCH format:
  - MAJOR version (1.x.x): Introduce breaking changes that are not backward-compatible.
  - MINOR version (1.1.x): Add new features that are backward-compatible.
  - PATCH version (1.1.1): Include bug fixes or minor improvements without changing functionality.
- Ensure that every time you release your library, you evaluate whether changes are breaking, new features, or just fixes, and adjust the version number accordingly.

2. Document breaking changes clearly
- Breaking changes should only be introduced in major version releases. Consumers will be aware that upgrading to a new major version might require code changes on their end.
- Provide detailed release notes for each major version, explaining which APIs were changed or deprecated and how consumers can migrate.
- Consider using deprecation warnings in minor versions before removing features in the next major version.

3. Use a CHANGELOG or Release Notes
- Maintain a CHANGELOG.md that outlines what has changed with each version release. Clearly separate breaking changes, new features, improvements, and bug fixes.
- Follow a clear structure to help users understand whether upgrading is safe or requires intervention.
- Example format:
```
## [1.2.0] - 2024-10-09
### Added
- New feature XYZ that allows ...

### Fixed
- Fixed a bug where ...

## [1.0.0] - 2023-01-15
### Breaking Changes
- Removed deprecated API `doSomethingOld()`, replaced with `doSomethingNew()`.
```

4. Communicate deprecations effectively
- Avoid removing APIs suddenly. Instead, mark them as deprecated first, provide alternatives, and only remove them in the next major release.
- When deprecating an API, add helpful warnings to guide consumers to the new API or feature.
- For example, in Swift, you can mark a function as deprecated and suggest an alternative:
```swift
@available(*, deprecated, message: "Use 'newFunction' instead.")
func oldFunction() {
    // Deprecated code
}
```

5. Avoid frequent major version changes
- Minimize breaking changes: Frequent major version changes disrupt users and force them to modify their code frequently. Consumers prefer stability.
- Plan your API changes carefully and batch breaking changes together when possible. This allows consumers to upgrade less often and with more confidence.

6. Ensure backward compatibility
- Keep as much backward compatibility as possible when releasing new versions, especially in minor and patch releases.
- If an API must be removed or significantly altered, provide a compatibility layer that allows both old and new APIs to coexist temporarily.
- Example:
```swift
// Old API
func performAction() {
    performNewAction()
}

// New API
func performNewAction() {
    // New implementation
}
```

7. Use automated testing for version compatibility
- Maintain comprehensive unit, integration, and regression tests to ensure that new versions don't introduce unexpected bugs.
- Set up CI (Continuous Integration) pipelines to automatically test your library across multiple versions of your dependencies (if applicable) to ensure compatibility and minimize breakage.

8. Tag versions in git
- When releasing a new version of your library, always tag the release in your version control system (e.g., Git) with the version number (e.g., v1.2.3).
- Tagging makes it easy for consumers to find the exact code associated with a particular release and for you to track changes over time.

9. Bundle only necessary code in releases
- Keep your library lightweight by including only the necessary code and assets in your releases.
- Avoid bundling experimental or unfinished features in stable releases. Use feature branches or pre-releases (like 1.0.0-beta) for unfinished work.

10. Offer pre-release versions for testing
- For significant changes or experimental features, release pre-release versions (e.g., 1.3.0-beta.1) to allow consumers to test upcoming changes before they are finalized.
- Pre-releases give you feedback from real users before committing to a major release.

11. Leverage Version Constraints in Dependencies
- If your library depends on other libraries, ensure that you specify version ranges that are as flexible as possible while still ensuring compatibility.
- For example, in Swift Package Manager, you might use:
```swift
.package(url: "https://github.com/another-lib.git", from: "1.0.0")
```
This allows your library to stay compatible with any 1.x.x version of the dependency.
- Avoid locking to exact versions unless absolutely necessary, as this can cause conflicts when your users try to integrate your library with other dependencies.

12. Release early and often
- Regularly release new versions of your library to ensure that consumers get timely access to bug fixes and new features.
- Keeping your library up-to-date reduces the pressure to release huge changes all at once, which can introduce more risk.

13. Bundle features thoughtfully
- When planning a release, especially a minor or major version, bundle related features together. This ensures that new functionality and breaking changes (if any) come in predictable, well-documented batches.
- Avoid including too many unrelated features in the same release, as this can increase the complexity of upgrading.

14. Version your API documentation
- Version your library's documentation alongside the code itself. This ensures that users can easily find the correct documentation for the version of the library they are using.
- Example: If your library has a website, include a dropdown to choose documentation for different versions.

15. Communicate with your users
- If your library is used by others (internally or publicly), establish communication channels where users can ask about versioning and provide feedback (e.g., GitHub issues, Slack, email).
- Keep users informed about upcoming breaking changes, new features, or deprecations.

16. Keep API surfaces minimal
- Limit the public API surface to avoid frequent breaking changes. If only necessary parts of your code are public, you'll have more freedom to refactor internal components without impacting users.
- Clearly distinguish between public APIs (designed for external use) and internal APIs (which can change freely).
