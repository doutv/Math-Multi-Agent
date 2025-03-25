# Math Multi-Agent System

## Overview

The Math Multi-Agent System is a collaborative AI framework designed to solve complex mathematical problems by leveraging multiple AI agents working in parallel with different solution strategies. The system combines the strengths of different language models (GPT-4 and Claude) with specialized tools to approach problems from multiple angles.

## System Architecture

### Core Components

1. **Main Orchestrator (`main.py`)**
   - Manages the overall workflow
   - Coordinates multiple agent processes
   - Collects and evaluates solutions
   - Produces final answer through consensus

2. **Calculation Module (`src/action/Calculate.py`)**
   - Provides symbolic and numerical calculation capabilities
   - Integrates with WolframAlpha API for complex math computations
   - Offers simple calculation functions through SymPy

3. **Programming Module (`src/action/Programmer.py`)**
   - Generates and executes Python code to solve problems programmatically
   - Uses GPT-4 to write specialized solution code
   - Manages code execution with timeout handling and error recovery

## Workflow

1. **Problem Input**
   - System takes a mathematical problem as input text

2. **Solution Strategy Generation**
   - Generates `m` different solution approaches (default: 5)
   - Each approach is assigned to a different agent

3. **Multi-Agent Parallel Processing**
   - Each agent works independently using its assigned approach
   - Agents alternate between GPT-4 and Claude models
   - Each agent can work for up to `n` rounds (default: 15)

4. **Agent Decision Cycle**
   - For each round, agent:
     1. Analyzes current state and progress
     2. Selects next action from available tools
     3. Executes action and processes results
     4. Updates its knowledge state
     5. Continues until solution found or max rounds reached

5. **Solution Aggregation**
   - Each agent's solution process is summarized
   - Solutions are collected with confidence ratings

6. **Final Evaluation**
   - Review agent evaluates all solutions
   - Determines most likely correct answer based on:
     - Consensus among agents
     - Quality of reasoning
     - Confidence ratings

## Available Actions/Tools

1. **`wolfram_alpha`**
   - Leverages WolframAlpha API for complex calculations
   - Handles advanced mathematical operations

2. **`simple_calculate`**
   - Performs basic calculations using SymPy
   - Parses and evaluates LaTeX expressions

3. **`deep_thinking`**
   - Conducts in-depth analysis of the problem
   - Generates insights and possible solution paths

4. **`deduction`**
   - Performs step-by-step logical reasoning
   - Focuses on formal mathematical proofs

5. **`programmer`**
   - Generates Python code to solve problems programmatically
   - Handles numerical simulations and algorithms
   - Executes code and processes results

6. **`Resolve`**
   - Finalizes the solution process
   - Presents agent's final answer

## Key Features

1. **Multi-Strategy Approach**
   - Explores multiple solution paths simultaneously
   - Reduces risk of getting stuck in suboptimal approaches

2. **Model Diversity**
   - Alternates between GPT-4 and Claude for different perspectives
   - Leverages strengths of different AI models

3. **Tool Integration**
   - Combines symbolic, numerical, and programming approaches
   - Accesses external computational resources (WolframAlpha)

4. **Consensus Mechanism**
   - Cross-validates results through multiple independent solutions
   - Increases reliability through agreement across agents

5. **Comprehensive Documentation**
   - Records complete solution processes
   - Provides confidence ratings and justifications

## Example Use Case

For a problem like the "Ghost Card" game analysis in the original code:
1. Different agents might approach it through:
   - Probability theory (analytical solution)
   - Game theory analysis
   - Numerical simulation via programming
   - Decision tree analysis
   - Recursive formula derivation

2. Each approach provides a different perspective, and the final review synthesizes these into a comprehensive solution.

## Technical Implementation

- Written in Python
- Uses OpenAI and Anthropic API clients
- Integrates with WolframAlpha
- Employs code generation and execution
- Implements timeout handling and error recovery
- Records solution processes in text files