[[Application Integration]]

> [!Definition]
> AWS Step Functions is a low-code visual workflow service used to orchestrate AWS services, automate business processes, and build serverless applications.

AWS Step Functions provides serverless orchestration for modern applications. Orchestration centrally manages a workflow by breaking it into multiple steps, adding flow logic, and tracking the inputs and outputs between the steps.

As your applications run, Step Functions maintains the application state, tracking exactly which workflow step your application is in, and stores an event log of data that is passed between application components. That means if the workflow is interrupted for any reason, your application can pick up right where it left off.

Step Functions is based on state machines and tasks. A state machine is a workflow. A task is a state in a workflow that represents a single unit of work that another AWS service performs. Each step in a workflow is a state.

### Different States in a State Machine

- Pass State : Passes it's input to the output
- Task State : Represents a single unit of work performed by a state machine
- Choice State : Provides a branching logic to the state machine
- Wait State : Delays the state machine, till a specified timestamp or a duration from the start of the state
- Success State : Stops an activity Successfully
- Fail State : Stops the activity of a state Machine and marks it as failure
- Parallel State : Create parallel branches of activity
- Map State : Can be used to run a set of steps for each element of an input array

### States and Transitions

A State is what unit of work a state machine performs, and transitions are the links which connect states together and define the State Machine

### States Language

Amazon states language is a JSON structured document which is used to define state machines and the transitions between the states

### Step Functions Workflow Studio

Workflow Studio for step functions is a low code visual workflow designer  

