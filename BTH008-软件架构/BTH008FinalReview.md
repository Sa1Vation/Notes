# BTH 008 FinalReview

## A: Definition Ch 1-3

### definition of SA (3P)  [Ch 1.1, pp4-7]

The software architecture of a system is the set of structures needed to reason about the system, which comprise software elements, relations among them, and properties of both.

### Summary

1. Every system has a software architecture, but this architecture may be documented and disseminated, or it may not be.
2. There is no such thing as an inherently good or bad architecture. Architec- tures are either more or less fit for some purpose.

### Structures categories (6P)  [Ch 1, pp10-17]

1. *Module structures* - Module describes how the system is to be structured as a set of code or data units that have to be constructed or procured.
   - *Decomposition structure.*
   - *Uses structure*
   - *Layer structure*
   - *Class (or generalization) structure*
   - *Data model*
2. *Component-and-connector* - C&C describe how the system is to be structured as a set of elements that have runtime behavior (components) and interactions (connectors).
   - *Service structure*
   - *Concurrency structure*
3. *Allocation structures* - Allocation structures describe how system will relate to non-software structures in its environment (CPU, file system etc.).
   - *Deployment structure*
   - *Implementation structure*
   - *Work assignment structure*

![Screen Shot 2021-06-23 at 6.05.13 PM](https://gitee.com/Sa1vation/my-pic-bed/raw/master/typora_imgs/20210628145602.png)

### What can you use a software architecture for (2P)   [Ch 2, pp25-33]

1. An architecture will **inhibit or enable a system’s driving quality attributes**. 架构将抑制或提高系统的关键质量属性。
2. The decisions made in an architecture allow you to **reason about and manage change as the system evolves**. 在架构中做出的决策使得您可以在系统发展时推理和管理更改。
3. The analysis of an architecture **enables early prediction of a system’s qualities**. 架构分析可以及早预测系统的质量。
4. A documented architecture **enhances communication among stakeholders**. 文档化的架构增强了利益相关者之间的沟通。
5. The architecture is **a carrier of the earliest and hence most fundamental, hardest-to-change design decisions**. 架构是最早、因此也是最基本、最难改变的设计决策的载体。
6. An architecture **defines a set of constraints on subsequent implementation**. 架构定义了一组对后续实现的约束。
7. The architecture **dictates the structure of an organization, or vice versa**. 架构决定了组织的结构，反之亦然。
8. An architecture can **provide the basis for evolutionary prototyping**. 架构可以为循序渐进的原型设计提供基础。
9. An architecture is the **key artifact that allows the architect and project manager to reason about cost and schedule**. 架构是允许架构师和项目经理推测成本和进度的关键工件。
10. An architecture can be **created as a transferable, reusable model that form the heart of a product line**. 可以创建可转移、可重用的架构模型，构成产品线的核心。
11. Architecture-based development **focuses attention on the assembly of components, rather than simply on their creation**. 基于架构的开发将注意力集中在组件的组装上，而不是简单地放在它们的创建上。
12. **By restricting design alternatives, architecture channels the creativity of developers, reducing design and system complexity.** 通过限制设计备选方案，架构可以引导开发人员的创造力，从而降低设计和系统的复杂性。
13. An architecture can be **the foundation for training a new team member**. 架构可以成为培训新团队成员的基础。

### software architecture influences from a technical perspective(2P) [Ch 2, pp25-33]

- Organizational influence:

## B: View Ch 18-20

### view definition and condition (8P) [From Lecture 3/4/5, ch18, pp331-341]

A view is a representation of a set of system elements and relations among them—not all system elements, but those of a particular type.

A view has:

1. Elements: All elements in the view must have a corresponding part in the view definition
2. Relations: Only relations that meet the selection criteria must be in the view
3. Properties: Properties must have values in the view
4. Selection criteria: A selection criterion for what kind of elements, relations and properties to include, Selection criteria can exclude certain elements or relations from the view.

 A view is consistent with its definition when: 

- All elements that fulfills the selection criterion is in the view
- All relations that fulfills the selection criterion is in the view
- That all properties that fulfills the selection criterion is in the view
- THAT NO addtional elements, relation or properties that does not meet the selection criterion is in the view

## C: Quality Attribute Ch4-12, 14

### ===Chapter 4===

### quality attribute scenario (12P)  [Ch 4 – figure 4.1, 4.2, pp68-70]

- Stimulus
- Stimulus source
- Response
- Response mesure
- Environment
- Artifact

![Screen Shot 2021-06-23 at 7.19.55 PM](https://gitee.com/Sa1vation/my-pic-bed/raw/master/typora_imgs/20210628145615.png)

### coordination model decisions (4P)  [Ch 4.6 pp 73-74]

- Identifying the elements of the system that must coordinate, or are prohibited from coordinating.
- Determining the properties of the coordination
  - such as timeliness, currency, completeness, correctness, and consistency.
- Choosing the communication mechanisms (between systems, between our system and external entities, between elements of our system) that realize those properties. 
  - Important properties of the communication mechanisms include stateful versus stateless, synchronous versus asynchronous, guar-anteed versus nonguaranteed delivery, and performance-related properties such as throughput and latency.

### asynchronous communication (4P)  [Ch 4.6 pp 73-74]

Asynchronous communication is any form of communication that doesn't require both people to be available at the same time — email is a classic example. Asynchronous communication simply means that the person you are “talking” to isn't consuming the information at the same time as you are producing it.

Synchronous communication is when you're talking with someone face to face - or on the phone, on a video call, or even chatting on Slack. You're both present at the same time, even if you aren't physically in the same space.

Asynchronous communication does not block the program thread until a response is ready.

Both asynchronous communication and synchronous communication can be used in the same system. 

### data-model (6P)  [ Ch 4.6 pp 74]

- Choosing the major data abstractions, their operations, and their properties. 
  - This includes determining how the data items are created, initialized, accessed, persisted, manipulated, translated, and destroyed.
- Compiling metadata needed for consistent interpretation of the data.
- Organizing the data. 
  - This includes determining whether the data is going to be kept in a relational database, a collection of objects, or both. If both, then the mapping between the two different locations of the data must be determined.

 

### ===Chapter 5===

### Heartbeat- and/or Ping/Echo- tactics (4P)  [ Ch 5.2 pp 87-89] 

- Ping/echo refers to an asynchronous request/response message pair ex-changed between nodes, used to determine reachability and the round-trip delay through the associated network path. But the echo also determines that the pinged component is alive and responding correctly.
- Heartbeat is a fault detection mechanism that employs a periodic message exchange between a system monitor and a process being monitored. 

### availability tactics (6P)  [Ch 5.2 pp 87-95]

- Detect faults
  - Ping / Echo
  - Monitor
  - Heartbeat
  - Timestamp
  - Sanity Checking
  - Condition Monitoring
  - Voting
  - Exception Detection
  - Self-Test
- Recover from faults
  - Preparation and Repair
    - Active Redundancy
    - Passive Redundancy
    - Spare
    - Exception Handling
    - Rollback
    - Software upgrade
    - Retry
    - Ignore Faulty Behavior
    - Degradation
    - Reconfiguration
  - Reintroduction
    - Shadow
    - State Resychronization
    - Escalating Restart
    - Non-Stop Forwarding
- Prevent faults
  - Removal from Service
  - Transactions
  - Predictive Model
  - Exception Prevention
  - Increase Competence Set

![Screen Shot 2021-06-23 at 7.49.04 PM](https://gitee.com/Sa1vation/my-pic-bed/raw/master/typora_imgs/20210628145659.png)

### fault tree analysis (6P)  [ Ch 5, pp 83]

 

### ===Chapter 7===

### modifiability tactic sub-category defer binding (6P) [Ch 7.2 pp 121-125]

- Reduce Size of a Module
  - Split Module
- Increase Cohesion
  - Increase Semantic Coherence
- Reduce Coupling
  - Encapsulate
  - Use and Intermediary
  - Restrict Dependencies
  - Refactor
  - Abstract Common Services
- Defer Binding
  - An architecture that is suitably equipped to accommodate modifications late in the life cycle will, on average, cost less than an architecture that forces the same modification to be made earlier. The preparedness of the system means that some costs will be zero, or very low, for late life-cycle modifications. This, however, neglects the cost of preparing the architecture for the late binding.

![Screen Shot 2021-06-23 at 7.51.03 PM](https://gitee.com/Sa1vation/my-pic-bed/raw/master/typora_imgs/20210628145707.png)

### the modifiability tactic Use an intermediary (4P)  [Ch 7.2 pp 121-125,]

- Use an intermediary breaks a dependency.

 

### ===Chapter 10===

### a general scenario for a Testability quality(4P)  [Ch 10]

![Screen Shot 2021-06-23 at 7.53.21 PM](https://gitee.com/Sa1vation/my-pic-bed/raw/master/typora_imgs/20210628145713.png)

### testability tactics (8P)  [Ch 10 pp 168]

- Control and Observe System State
  - Specialized Interfaces
  - Record / Playback
  - Localize State Storage
  - Abstract Data Sources
  - Sandbox
  - Executable Assertions
- Limit Complexity
  - Limit Structural Complexity
  - Limit Nondeterminism

![Screen Shot 2021-06-23 at 7.53.53 PM](https://gitee.com/Sa1vation/my-pic-bed/raw/master/typora_imgs/20210628145719.png) 

### ===Chapter 13===

### an architectural pattern (3P)  [Ch 13.1 pp 203-205]

An architectural pattern 设计模式

- is a package of design decisions that is found in practice repeatedly, 是一组经常在实践中出现的设计决策
- has known properties that permit reuse, and  具有可复用性
- describe a class of architectures. 描述了一类架构

An architectural pattern establishes a relationship between: 设计模式描述了场景、问题和解决方案之间的关系

- A context
- A problem
- A solution 解决方案包括
  - A set of element types (for example, data repositories, processes, and objects) 一组元素类型
  - A set of interaction mechanisms or connectors (for example, method calls, events, or message bus) 一组交互机制或连接器
  - A topological layout of the components 组件的拓扑结构
  - A set of semantic constraints covering topology, element behavior, and interaction mechanisms 一组涵盖拓扑、元素行为和交互机制的语义约束

- **Module Patterns**
  - Layered Pattern
- **Component-and-Connector Patterns**
  - Broker Pattern
  - Model-View-Controller Pattern
  - Pipe-and-Filter Pattern
  - Client-Server Pattern
  - Peer-to-Peer Pattern
  - Service-Oriented Architecture Pattern
  - Publish-Subscribe Pattern
  - Shared-Data Pattern
- **Allocation Patterns**
  - Map-Reduce Pattern
  - Multi-tier Pattern

### ===Chapter 4-11===

### Run-time/Development time quality attribute (4P)  [From the lectures]

- Run-time quality
  - Performance (Latency, Speed)
  - Availability (Failure Rate, Downtime Percentage)
  - Interoperability (Exchange Infomation Effectiveness)
  - Security (Confidentiality, Integrity, Availability)
  - Usability (Time cost of Accomplish a Task)
  - *Scalability
  - *Safety
- Development-time quality (observable during development)
  - Modifiability (Ease of make a change)
  - Testability (Same test can cover more code of software)
  - *Variability
  - *Portability
  - *Scalability
  - *Development distributability

### the tactics with the correct quality (8P)  [Ch7/8/9/10, Performance, Modifiability, Security, Testability]

#### Performance

- Control Resource Demand
  - Manage Sampling Rate
  - Limit Event Response
  - Prioritize Events
  - Reduce Overhead
  - Bound Execution Times
  - Increase Resource Efficiency
- Manage Resources
  - Increase Resources
  - Introduce Concurrency
  - Maintain Multiple Copies of Computations
  - Maintain Multiple Copies of Data
  - Bound Queue Sizes
  - Schedule Resources

![Screen Shot 2021-06-27 at 1.56.14 PM](https://gitee.com/Sa1vation/my-pic-bed/raw/master/typora_imgs/20210628145724.png)

#### Modifiability

- Reduce Size of a Module
  - Split Module
- Increase Cohesion
  - Increase Semantic Coherence
- Reduce Coupling
  - Encapsulate
  - Use and Intermediary
  - Restrict Dependencies
  - Refactor
  - Abstract Common Services
- Defer Binding
  - An architecture that is suitably equipped to accommodate modifications late in the life cycle will, on average, cost less than an architecture that forces the same modification to be made earlier. The preparedness of the system means that some costs will be zero, or very low, for late life-cycle modifications. This, however, neglects the cost of preparing the architecture for the late binding.

#### Security

- Detect Attacks
  - Detect Intrusion
  - Detect Service Denial
  - Verify Service Integrity
  - Detect Message Delay
- Resist Attacks
  - Identify Actors
  - Authenticate Actors
  - Authorize Actors
  - Limit Access
  - Limit Exposure
  - Encrypt Data
  - Separate Entities
  - Change Default Settings
- React to Attacks
  - Revoke Access
  - Lock Computer
  - Inform Actors
- Recover from Attacks
  - Maintain Audit Trail
  - Restore
    - See Availability

![Screen Shot 2021-06-27 at 1.50.14 PM](https://gitee.com/Sa1vation/my-pic-bed/raw/master/typora_imgs/20210628145729.png)

#### Testability

- Control and Observe System State
  - Specialized Interfaces
  - Record / Playback
  - Localize State Storage
  - Abstract Data Sources
  - Sandbox
  - Executable Assertions
- Limit Complexity
  - Limit Structural Complexity
  - Limit Nondeterminism

### General Secenario

![Screen Shot 2021-06-29 at 3.35.56 PM](https://gitee.com/Sa1vation/my-pic-bed/raw/master/typora_imgs/20210629153656.png)

![Screen Shot 2021-06-29 at 3.37.31 PM](https://gitee.com/Sa1vation/my-pic-bed/raw/master/typora_imgs/20210629153736.png)

![Screen Shot 2021-06-29 at 3.38.00 PM](https://gitee.com/Sa1vation/my-pic-bed/raw/master/typora_imgs/20210629153805.png)

![Screen Shot 2021-06-29 at 3.38.24 PM](https://gitee.com/Sa1vation/my-pic-bed/raw/master/typora_imgs/20210629153828.png)

![Screen Shot 2021-06-29 at 3.38.53 PM](https://gitee.com/Sa1vation/my-pic-bed/raw/master/typora_imgs/20210629153903.png)

![Screen Shot 2021-06-29 at 3.39.24 PM](https://gitee.com/Sa1vation/my-pic-bed/raw/master/typora_imgs/20210629153929.png)

![Screen Shot 2021-06-29 at 3.39.45 PM](https://gitee.com/Sa1vation/my-pic-bed/raw/master/typora_imgs/20210629153949.png)

