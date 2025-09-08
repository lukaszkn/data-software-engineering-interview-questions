# Apache Airflow
Apache Airflow

* [What is Airflow?](#What-is-Airflow)
* [What issues does Airflow resolve?](#What-issues-does-Airflow-resolve)
* [Explain how workflow is designed in Airflow?](#Explain-how-workflow-is-designed-in-Airflow)
* [Explain Airflow Architecture and its components?](#Explain-Airflow-Architecture-and-its-components)
* [What are the types of Executors in Airflow?](#What-are-the-types-of-Executors-in-Airflow)
* [What are the pros and cons of SequentialExecutor?](#What-are-the-pros-and-cons-of-SequentialExecutor)
* [What are the pros and cons of LocalExecutor?](#What-are-the-pros-and-cons-of-LocalExecutor)
* [What are the pros and cons of CeleryExecutor?](#What-are-the-pros-and-cons-of-CeleryExecutor)
* [What are the pros and cons of KubernetesExecutor?](#What-are-the-pros-and-cons-of-KubernetesExecutor)
* [How to define a workflow in Airflow?](#How-to-define-a-workflow-in-Airflow)
* [How do you make the module available to airflow if you're using Docker Compose?](#How-do-you-make-the-module-available-to-airflow-if-you-re-using-Docker-Compose)
* [How to schedule DAG in Airflow?](#How-to-schedule-DAG-in-Airflow)
* [What is XComs In Airflow?](#What-is-XComs-In-Airflow)
* [What is xcom_pull in XCom Airflow?](#What-is-xcom-pull-in-XCom-Airflow)
* [What is Jinja templates?](#What-is-Jinja-templates)
* [How to use Airflow XComs in Jinja templates?](#How-to-use-Airflow-XComs-in-Jinja-templates)

## What is Airflow?
Apache Airflow is an open-source platform for developing, scheduling, and monitoring batch-oriented workflows. It allows you to author workflows as Directed Acyclic Graphs (DAGs) of tasks. Airflow's rich user interface makes it easy to visualize pipelines running in production, monitor progress, and troubleshoot issues when needed. It's highly extensible, allowing you to define your own operators and executors, and it can be scaled to handle a large number of workflows.

[Top](#top)

## What issues does Airflow resolve?
Airflow addresses several key issues in data engineering and workflow management:
*   **Scheduling and Automation:** It replaces cron jobs with a more powerful and flexible system for scheduling tasks.
*   **Dependency Management:** It allows you to define complex dependencies between tasks, ensuring that a task only runs when its prerequisites are met.
*   **Monitoring and Alerting:** It provides a centralized view of all workflows, making it easy to monitor their status, view logs, and set up alerts for failures.
*   **Scalability:** It can be scaled out to handle a large number of concurrent tasks and workflows.
*   **Extensibility:** It allows you to create custom operators, hooks, and executors to fit your specific needs.
*   **Backfilling:** It allows you to easily re-run tasks for a specific historical period.

[Top](#top)

## Explain how workflow is designed in Airflow?
In Airflow, a workflow is designed as a Directed Acyclic Graph (DAG). A DAG is a collection of all the tasks you want to run, organized in a way that reflects their relationships and dependencies. Each node in the graph is a task, and the directed edges represent the dependencies between tasks. For example, an edge from task A to task B means that task A must be completed successfully before task B can begin. The "Acyclic" part of the name means that there are no circular dependencies, which ensures that the workflow has a clear start and end. DAGs are defined in Python scripts, which gives you the flexibility to use code to generate your workflows dynamically.

[Top](#top)

## Explain Airflow Architecture and its components?
Airflow's architecture consists of several key components:
*   **Web Server:** A Flask-based web server that provides the user interface. It allows you to monitor and manage your DAGs, view task logs, and see the status of your workflows.
*   **Scheduler:** The heart of Airflow. It's a persistent service that monitors all of your DAGs and triggers the tasks whose dependencies have been met.
*   **Metastore Database:** A database (e.g., PostgreSQL, MySQL) that stores the state of all tasks and workflows. It keeps track of which tasks have run, their status, and other metadata.
*   **Executor:** The component that actually runs the tasks. Airflow has several types of executors, such as the `SequentialExecutor`, `LocalExecutor`, `CeleryExecutor`, and `KubernetesExecutor`.
*   **Worker (for CeleryExecutor and KubernetesExecutor):** These are the processes that actually execute the task logic. In a distributed setup, you can have multiple workers running on different machines.

[Top](#top)

## What are the types of Executors in Airflow?
Airflow has several types of executors:
*   **SequentialExecutor:** Runs one task at a time in a single process. It's the default executor and is useful for debugging, but not for production.
*   **LocalExecutor:** Runs tasks in parallel on a single machine. It's a good choice for small to medium-sized deployments.
*   **CeleryExecutor:** A distributed executor that uses a Celery backend (e.g., RabbitMQ, Redis) to distribute tasks to a pool of workers. It's a good choice for large-scale deployments.
*   **KubernetesExecutor:** A distributed executor that creates a new pod for each task in a Kubernetes cluster. It's a good choice for deployments that are already running on Kubernetes.
*   **CeleryKubernetesExecutor:** A hybrid executor that uses Celery to queue tasks and the KubernetesExecutor to run them.

[Top](#top)

## What are the pros and cons of SequentialExecutor?
*   **Pros:**
    *   Simple to set up and use.
    *   Good for debugging and testing.
    *   No external dependencies.
*   **Cons:**
    *   Not scalable. It can only run one task at a time.
    *   Not suitable for production.
    *   Single point of failure.

[Top](#top)

## What are the pros and cons of LocalExecutor?
*   **Pros:**
    *   Allows for parallel execution of tasks on a single machine.
    *   Relatively easy to set up.
    *   Good for small to medium-sized deployments.
*   **Cons:**
    *   Limited by the resources of a single machine.
    *   Single point of failure (the machine running the scheduler and executor).

[Top](#top)

## What are the pros and cons of CeleryExecutor?
*   **Pros:**
    *   Highly scalable. It can distribute tasks to a large number of workers.
    *   Fault-tolerant. If a worker goes down, the task can be rescheduled on another worker.
    *   Good for large-scale production deployments.
*   **Cons:**
    *   More complex to set up and maintain. It requires a Celery backend (e.g., RabbitMQ, Redis).
    *   Higher operational overhead.

[Top](#top)

## What are the pros and cons of KubernetesExecutor?
*   **Pros:**
    *   Highly scalable and fault-tolerant.
    *   Dynamically allocates resources for each task.
    *   Good for deployments that are already running on Kubernetes.
    *   Isolates task dependencies.
*   **Cons:**
    *   Requires a Kubernetes cluster.
    *   Can have a higher latency for starting tasks due to pod creation overhead.

[Top](#top)

## How to define a workflow in Airflow?
A workflow in Airflow is defined as a Python script that creates a DAG object. Here are the basic steps:
1.  **Import necessary modules:** `from airflow import DAG`, `from airflow.operators.bash_operator import BashOperator`, etc.
2.  **Define default arguments:** Create a dictionary of default arguments that will be applied to all tasks in the DAG.
3.  **Instantiate a DAG:** Create a DAG object with a unique `dag_id`, a `start_date`, a `schedule_interval`, and the `default_args`.
4.  **Define tasks:** Create instances of operators (e.g., `BashOperator`, `PythonOperator`) to define the tasks in your workflow.
5.  **Set dependencies:** Use the `>>` and `<<` operators to define the dependencies between tasks.

[Top](#top)

## How do you make the module available to airflow if you're using Docker Compose?
To make a module available to Airflow when using Docker Compose, you can use a volume mount. In your `docker-compose.yml` file, you can mount a local directory containing your custom modules into the Airflow containers (scheduler, webserver, and workers). For example:
```yaml
volumes:
  - ./dags:/usr/local/airflow/dags
  - ./plugins:/usr/local/airflow/plugins
  - ./my_modules:/usr/local/airflow/my_modules
```
Then, you need to make sure that the directory containing your modules is in the Python path. You can do this by setting the `PYTHONPATH` environment variable in your `docker-compose.yml` file.

[Top](#top)

## How to schedule DAG in Airflow?
A DAG is scheduled in Airflow using the `schedule_interval` argument when you instantiate the DAG object. The `schedule_interval` can be a cron expression (e.g., `'0 0 * * *'` for daily), a `datetime.timedelta` object, or one of the cron presets (e.g., `'@daily'`, `'@hourly'`). Airflow will then automatically create DAG runs for each schedule interval that has passed since the DAG's `start_date`.

[Top](#top)

## What is XComs In Airflow?
XComs (short for "cross-communications") are a mechanism for tasks to pass small amounts of data to each other. They are a key-value store where the key is the `task_id` and the value is the data that was pushed by that task. XComs are useful for passing small pieces of information, such as a file path, a database query result, or a configuration parameter, from one task to another.

[Top](#top)

## What is xcom_pull in XCom Airflow?
`xcom_pull` is a method that allows a task to retrieve a value that was pushed to XComs by another task. You can specify the `task_id` of the task that pushed the value, and the key of the value you want to retrieve. If you don't specify a `task_id`, it will pull the value from the most recent task that pushed a value.

[Top](#top)

## What is Jinja templates?
Jinja is a modern and designer-friendly templating engine for Python. It allows you to generate dynamic content by embedding expressions and logic inside of a template file. In Airflow, Jinja templates are used extensively to parameterize tasks. You can use Jinja templates to pass dynamic information, such as the execution date, to your tasks. Many operator parameters are templated, which means you can use Jinja expressions in them.

[Top](#top)

## How to use Airflow XComs in Jinja templates?
Airflow XComs can be accessed in Jinja templates using the 'ti.xcom_pull' method, where 'ti' is the task instance available in the template context. This allows dynamic retrieval of data pushed by other tasks, enabling parameterization of commands, queries, or file paths within templated fields.

[Top](#top)
