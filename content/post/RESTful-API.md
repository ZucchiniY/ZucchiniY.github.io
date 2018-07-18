---
title: "Springboot RESTful API 构建"
date: 2018-04-28T19:51:02+08:00
draft: false
tags: ["RESTful","API"]
categories: ["Springboot"]
author: "Dylan Yang"
---

# RESTful 风格

RESTful 即不是标准也不是一般设计思想，而是一种架构风格、设计风格，或者说是一种设计原则。主要用于客户端和服务器交互类软件设计。

基于这个风格设计的软件可以更简洁，更有层次，更易于实现缓存等机制。
<!--more-->

|请求类型|URL|功能说明|
|-----|-----|------|
|GET|/users|查询|
|POST|/users|创建|
|GET|/users/id|根据id查询|
|PUT|/users/id|根据id更新|
|DELETE|/users/id|根据id删除|

- `@Controller`: 修饰 `class` ，用来创建处理 *http* 请求的对象
- `@RestController`: 可以直接返回 `json` 格式，代替原本的 `@Controller` 和 `@ResponseBody` 修饰符
- `@RequestMapping`: 配置 *url* 映射

``` java
@RestController 
@RequestMapping(value="/users") //父节点
public class UserController { 

    // 创建线程安全的Map
    static Map<Long, User> users = Collections.synchronizedMap(new HashMap<Long, User>()); 

    @RequestMapping(value="/", method=RequestMethod.GET) 
    public List<User> getUserList() { 
        // 处理"/users/"的GET请求，用来获取用户列表 
        // 还可以通过@RequestParam从页面中传递参数来进行查询条件或者翻页信息的传递 
        return user; 
    } 

    @RequestMapping(value="/", method=RequestMethod.POST) 
    public String postUser(@ModelAttribute User user) { 
        // 处理"/users/"的POST请求，用来创建User 
        // 除了@ModelAttribute绑定参数之外，还可以通过@RequestParam从页面中传递参数 
        return "success"; 
    } 

    @RequestMapping(value="/{id}", method=RequestMethod.GET) 
    public User getUser(@PathVariable Long id) { 
        // 处理"/users/{id}"的GET请求，用来获取url中id值的User信息 
        // url中的id可通过@PathVariable绑定到函数的参数中 
        return users.get(id); 
    } 

    @RequestMapping(value="/{id}", method=RequestMethod.PUT) 
    public String putUser(@PathVariable Long id, @ModelAttribute User user) { 
        // 处理"/users/{id}"的PUT请求，用来更新User信息
        return "success"; 
    } 

    @RequestMapping(value="/{id}", method=RequestMethod.DELETE) 
    public String deleteUser(@PathVariable Long id) { 
        // 处理"/users/{id}"的DELETE请求，用来删除User
        return "success"; 
    }
}
```