---
id: skill-001-hello-world
name: hello-world
version: 1.0.0
description: 示例 skill - 演示基本的 skill 结构和通信
directory: _generated/
upstream: []
downstream: []
inputs:
  - name: name
    type: string
    required: false
    description: 要问候的名称
outputs:
  - name: greeting
    type: string
    description: 生成的问候语
  - name: timestamp
    type: string
    description: 执行时间戳
created_by: genesis
created_at: 2026-01-14
updated_at: 2026-01-14
tags:
  - generated
  - example
  - demo
---

# Hello World Skill

> 一个简单的示例 skill，演示基本的输入输出和状态管理

## Instructions

当用户调用 `/hello-world` 时：

### Step 1: 获取输入

检查是否提供了 `name` 参数：
- 如果提供了: 使用该名称
- 如果未提供: 使用 "World" 作为默认值

### Step 2: 生成问候语

创建问候语: `"Hello, <name>! Welcome to the self-evolving skill system."`

### Step 3: 更新状态

更新 `./context/state.json`:

```json
{
  "data": {
    "skill-001-hello-world": {
      "status": "completed",
      "completed_at": "<current-timestamp>",
      "input": { "name": "<input-name>" },
      "output": {
        "success": true,
        "data": {
          "greeting": "Hello, <name>! Welcome to the self-evolving skill system.",
          "timestamp": "<current-timestamp>"
        }
      }
    }
  }
}
```

### Step 4: 响应用户

向用户显示：
```
✨ Hello World Skill Executed ✨

Greeting: Hello, <name>! Welcome to the self-evolving skill system.
Timestamp: <timestamp>

This is a demo skill created by Genesis to showcase the skill system.
```

## Communication

### Reading State
此 skill 没有上游依赖，直接从用户输入获取数据。

### Writing State
```json
{
  "data": {
    "skill-001-hello-world": {
      "status": "completed",
      "output": {
        "greeting": "...",
        "timestamp": "..."
      }
    }
  }
}
```

## Error Handling

这是一个简单的 skill，几乎不会出错。如果出现意外错误：
1. 记录错误到 state.json
2. 返回友好的错误消息

## Examples

### Example 1: 带参数调用

```
/hello-world name="Claude"
```

输出:
```
✨ Hello World Skill Executed ✨

Greeting: Hello, Claude! Welcome to the self-evolving skill system.
Timestamp: 2026-01-14T10:00:00Z
```

### Example 2: 无参数调用

```
/hello-world
```

输出:
```
✨ Hello World Skill Executed ✨

Greeting: Hello, World! Welcome to the self-evolving skill system.
Timestamp: 2026-01-14T10:00:00Z
```
