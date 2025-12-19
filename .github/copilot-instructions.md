---
description: AI rules derived by SpecStory from the project AI interaction history
globs: *
---

## <headers/>

## TECH STACK

## PROJECT DOCUMENTATION & CONTEXT SYSTEM

## CODING STANDARDS

## WORKFLOW & RELEASE RULES

## DEBUGGING

## SECURITY PROTOCOLS

### Tool Call Interception and Evaluation

The system must include a mechanism to intercept, evaluate, and potentially cancel tool calls initiated by the AI. This is especially critical for potentially destructive commands, such as those that could lead to data loss. The current rules strictly prohibit deleting anything, and this policy must be enforced through the interception and evaluation process. The interception must occur at the gateway layer, before any tool call is dispatched to its handler or executor. The evaluation logic must parse the tool call payload, identify the operation (e.g., command, arguments), and check for prohibited actions (such as deletion). If a violation is detected, the gateway must not forward the call and must return a clear error indicating the policy violation. This logic should be implemented as a middleware, filter, or interceptor, depending on your gateway’s architecture (HTTP, gRPC, or custom). The mechanism must be in place for all tool calls, not just for terminal commands. The evaluation must be comprehensive and block any operation that could lead to data loss or policy violation. If a tool call violates the policy, the system must return an error for any blocked operation.