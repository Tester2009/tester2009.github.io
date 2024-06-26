---
title: "Building a Scalable Web Application: Integrating React.js, Nginx Load Balancer, and Python Flask APIs with MongoDB"
tags:
- Web Development
- React.js
- Nginx
- Load Balancing
- Python Flask
- RESTful APIs
- MongoDB
- Horizontal Scalability
- Docker Compose
---


Building and deploying fullstack web application today is different, compared to during the old times. Technologies has advanced further and allow us to keep our work standardise, simple, and faster.

Following is the diagram of the architecture:

```
                 Docker | Containerized Applications                                                                                             
                ┌───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────┐
                │                                                                                                                               │
                │                                                                    '/' GET                                                    │
                │                                                                                                                               │
                │                                                                    '/create' POST                                             │
                │                                                                                                                               │
                │                                                                    ┌───────────────────┐                                      │
                │                                                                    │                   │                                      │
                │                                                              ┌────►│ flask | backend-1 ├─────┐                                │
                │                                                              │     │                   │     │                                │
                │                                                              │     └───────────────────┘     │                                │
                │                                                              │                               │        ┌────────────────────┐  │
┌─────────┐     │  ┌────────────────────┐         ┌──────────────────────┐     │                               │        │                    │  │
│         │     │  │                    ├────────►│                      ├─────┘                               ├───────►│ MongoDB | database │  │
│ Visitor ├─────┼─►│ reactjs | frontend │         │ nginx | loadbalancer │                                     │        │                    │  │
│         │     │  │                    │◄────────┤                      ├─────┐                               │        └────────────────────┘  │
└─────────┘     │  └────────────────────┘         └──────────────────────┘     │     ┌───────────────────┐     │                                │
                │                                                              │     │                   │     │                                │
                │                                                              │     │ flask | backend-2 ├─────┘                                │
                │                                                              └────►│                   │                                      │
                │                                                                    └───────────────────┘                                      │
                │                                                                                                                               │
                │                                                                    '/update' PUT                                              │
                │                                                                                                                               │
                │                                                                    '/delete' DELETE                                           │
                │                                                                                                                               │
                └───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────┘
                                                                                                                                                 
                                                                                                                                                 
                                                                                                                 Made by Muazzam @ Hakase        
                                                                                                                 26/06/2024                      
                                                                                                                                                 
                                                                                                                 made possible at: asciiflow.com 
```

Based on the diagram above, there is one container for handling frontend, then forward the request to one load-balancer, and forward again the request to one of the backend, depends on the URL path. If the request are '/' with GET method, and '/create' with POST method, backend-1 container will process the request, while if the request are '/update' with PUT method, and '/delete' with DELETE method, backend-2 container will process the request.


to be continue...