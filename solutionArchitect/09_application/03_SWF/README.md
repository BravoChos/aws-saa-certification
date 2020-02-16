# Amazon SWF
The fundamental concept in Amazon SWF is the workflow. A workflow is a set of activities that carry out some objective, together with logic that coordinates the activities. For example, a workflow could receive a customer order and take whatever actions are necessary to fulfill it. It coordinates work across distributed application components, helps implement complex business processes and application workflows, long running execution, and enables complex interactions between different applications on different platform, AWS and on-premise infrastructure and, different users.

In the process of carrying out the workflow, some activities may need to be performed more than once, perhaps with varying inputs. For example, in a customer-order workflow, you might have an activity that handles purchased items. If the customer purchases multiple items, then this activity would have to run multiple times. Amazon SWF has the concept of an activity task that represents one invocation of an activity. In our example, the processing of each item would be represented by a single activity task.

An **activity worker** is a program that receives activity tasks, performs them, and provides results back. Note that the task itself might actually be performed by a person, in which case the person would use the activity worker software for the receipt and disposition of the task. An example might be a statistical analyst, who receives sets of data, analyzes them, and then sends back the analysis.

The coordination logic in a workflow is contained in a software program called a **decider**. The decider schedules activity tasks, sprovides input data to the activity workers, processes events that arrive while the workflow is in progress, and ultimately ends (or closes) the workflow when the objective has been completed.

## How Amazon SWF Works
Using the Amazon Simple Workflow Service (Amazon SWF), you can implement distributed, asynchronous applications as workflows. Workflows coordinate and manage the execution of activities that can be run asynchronously across multiple computing devices and that can feature both sequential and parallel processing.

An SWF **Decision task** tells a decider that the state of the workflow execution has changed so that the decider can determine the next activity that needs to be performed .The **Decision task** contains the current workflow history.

Amazon SWF interacts with activity workers and deciders by providing them with work assignments known as tasks. There are three types of tasks in Amazon SWF:
- **Activity task** – An Activity task tells an activity worker to perform its function, such as to check inventory or charge a credit card. The activity task contains all the information that the activity worker needs to perform its function.
- **Lambda task** – A Lambda task is similar to an Activity task, but executes a Lambda function instead of a traditional Amazon SWF activity. For more information about how to define a Lambda task, see AWS Lambda Tasks.
- **Decision task** – A Decision task tells a decider that the state of the workflow execution has changed so that the decider can determine the next activity that needs to be performed. The decision task contains the current workflow history.

## Amazon SWF Limits
Maximum registered SWF domains: **100**  
Maximum SWF request size per request: **1 MB**  
Maximum workflow execution time: **1 year**

