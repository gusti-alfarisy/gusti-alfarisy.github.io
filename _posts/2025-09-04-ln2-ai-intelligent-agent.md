---
title: "Lecture Notes 2: Intelligent Agent"
date: 2025-09-04
background: "https://roughnotes.com/wp-content/uploads/2025/06/1_0707-Technology_683x366.jpg"

author: Gusti Ahmad Fanshuri Alfarisy
#tags: [Shared tag, 👩‍🔬 Emoji tag, "Special /?{:å characters", " Whitespace before and after "]
tags: [Artificial Intelligence, Agent]
comments: true
toc: true
---

## Agent and Environment

An agent is any entities that percept the environment through sensors and act using actuator based on the environment

![Illustration of an agent](https://i.sstatic.net/qIpUW.png)

percept sequence is the complete history that an agent has perceived

![A simple vacuum cleaner with two actions](/assets/theme/images/posts/simple_vacuum_cleaner.png)

How about calculator?

## Good Behaviour of an Agent

### Performance Measures

What supposed to be the good performance measures for vacuum cleaner?

The amount of dirt sucked? Is there a problem with this measure?

*"As a general rule, it is better to design performance measures according to what one actually wants to be achieved in the environment, rather than according to how one thinks the agent should behave"*

### Rationality

Rationale at any given time depends on several points:

* The performance measure that defines the criterion of success.
* The agent’s prior knowledge of the environment.
* The actions that the agent can perform.
* The agent’s percept sequence to date.

The definition of rationale agent:

*"For each possible percept sequence, a rational agent should select an action that is expected to maximize its performance measure, given the evidence provided by the percept sequence and whatever built-in knowledge the agent has."*

Is the simple vacuum-cleaner agent rationale?

### Omniscience, Learning, and Autonomy

Omniscient for an agent is impossible in reality.

Example: Walking on the road to say hello to an old friend across the street

**Rationality $$\neq$$ Perfection**

Don't you think being aware of unknown is beneficial? Open-World Lifelong Learning?

## The Nature of Environment

In order to create a rationale agent, Performance, Environment, Actuators, and Sensors need to be specified.

| Agent Type | Performance Measure | Environment | Actuators |
| ---------- | ------------------- | ----------- |-----------|
| Taxi driver | Safe, fast, legal, comfortable trip, maximize profits, minimize impact on other road users. | Roads, other traffic, police, pedestarians, customers, weather. | Steering, accelerator, brake, signal, horn, display, speech. | Cameras, radar, speedometer, GPS, engine, sensors, accelerometer, microphones, touchscreen. |
| Medical diagnosis system | Healthy patient, reduced costs | patient, hospital, staff | Display of questions, tests, diagnoses, treatments. | Touchscreen/voice entry of symptoms and finding |
| Interactive Programming Tutor?| ??? | ??? | ??? | ??? |

### Properties of Task Environment

* Fully observable vs partially observable
* Single-agent vs multiagent
* Deterministic vs nondeterministic, stochastic?
* Episodic vs sequential
* Static vs dynamic, semidynamic?
* Discrete vs continuous
* Known vs unknown


| Task environment | Observable | Agents | Deterministic | Episodic | Static | Discrete |
| -------------- | ------- |--------|------| ------- | -------- | ------- |
| Crossword puzzle | Fully | Single | Deterministic | Sequential | Static | Discrete |
| Chess with a clock | Fully | Multi  | Deterministic | Sequential | Semi | Discrete |
| Taxi driving | Partially | Multi | Stochastic | Sequential | Dynamic | Continuous |
| Interactive Programming Tutor? | ??? | ??? | ??? | ??? | ??? | ??? |

## The Structure of an Agent

*"The job of AI is to design an agent program that implements an agent function"*

With the assumption that AI will run on a device with actuator and sensor, the agent architecture is

agent = architecture + program

```
function TABLE-DRIVEN-AGENT(percept) returns an action
    persistent: percepts, a sequence, initially empty
                table, a table of actions, indexed by percept sequences, initially fully specified

append percept to the end of percepts
action ← LOOKUP(percepts, table)
return action
```

The size of lookup table will be:

$$
\sum_{t=1}^T= |P|^t
$$

Where $$P$$ is all possible percepts in a set and $$T$$ is the lifetime of an agent.


Automated taxi driver with 8 cameras:
* 70 megabytes per second (30 frames per second, 1080 × 720 pixels with 24 bits of color information)
* yielding a lookup table with over $$10^{600,000,000,000}$$ entries for an hour’s driving
* compared to the number of atoms in the observable universe is less than $$10^{80}$$


* (a) no physical agent in this universe will have the space to store the table; 
* (b) the designer would not have time to create the table; 
* and (c) no agent could ever learn all the right table entries
from its experience.

*"The key challenge for AI is to find out how to write programs that, to the extent possible, produce rational behavior from a smallish program rather than from a vast table"*

*"four basic kinds of agent programs that embody the principles underlying almost all intelligent systems: Simple reflex agents; Model-based reflex agents; Goal-based agents; and Utility-based agents"*

### Simple Reflex Agents


![simple reflex agent](/assets/theme/images/posts/simple_reflex_agent.png)

Source: (Russel and Norvig, 2022)

```
function REFLEX-VACUUM-AGENT([location,status]) returns an action
    if status = Dirty then return Suck
    else if location = A then return Right
    else if location = B then return Left
```

```
function SIMPLE-REFLEX-AGENT(percept) returns an action
    persistent: rules, a set of condition–action rules

    state ← INTERPRET-INPUT(percept)
    rule ← RULE-MATCH(state, rules)
    action ← rule.ACTION
    return action
```

### Model-based Reflex Agents

![model-based reflex agent](/assets/theme/images/posts/model_based_agent.png)

```
function MODEL-BASED-REFLEX-AGENT(percept) returns an action
    persistent: state, the agent’s current conception of the world state
                transition model, a description of how the next state depends on the current state and action 
                sensor model, a description of how the current world state is reflected in the agent’s percepts
                rules, a set of condition–action rules
                action, the most recent action, initially none

    state ← UPDATE-STATE(state, action, percept, transition model, sensor model)
    rule ← RULE-MATCH(state, rules)
    action ← rule.ACTION
    return action
```

### Goal-based Agents


![goal-based agent](/assets/theme/images/posts/goal_based_agent.png)

### Utility-based Agents


![utility-based agent](/assets/theme/images/posts/utility_based_agent.png)


### Learning Agents

![learning agents](/assets/theme/images/posts/learning_agents.png)

## Assignment

Please specify the PEAS (Performance, Environment, Actuators, and Sensors) of the AI agent provided below as well as the properties of the environment. Describe each specification that you justify. 

Then, specify the different structure of the agents based on your choice of AI agents. Please describe Goal-based agent, Utility-based agent, and Learning agents for your topic.

Please submit next week on LMS week 2, before **17 September 2025**!

### Automatic plant species identification through mobile device

The users can use their mobile phone to take a picture of plant in any environment and the agent can predict what species it is with the relevant information. The agent can provide unidentified species if the species is not available in the agent knowledge. 

### Chatbot for Academic Information in University

The students in university can ask/query for retrieving relevant information. For example when discussing about the timeline of academic calender, querying about when the final proposal can be submitted, or any other academic information like how to write the proposal or final projects.

### Automatic Biodiversity Monitoring using Camera sensors

The camera can capture different living species on an environment and map the biodiversity level in that environment along with the number of species found in that area. The system can provide information about low, medium, or high biodiversiy along with the availability of the invasive species.

### Focused Web Crawler for Academic Journal

The users can query about the topic of journal (e.g. "kecerdasan buatan untuk chatbot") that return a list of clickable journal that related to the topic. The user can leave the bot for several ours or even days, and the users will receive the collected relevant journals.