---
layout: post
title: An Overview of Microservices Architecture
---

An introduction to the trending Microservices Archicture. In this post we will discuss about how microservices work, what are the benefits and what should we look out for when implementing it.

### What is Microservices Architecture?

>  A particular way of designing software applications as suites of independently deployable services
>
> &mdash; <cite>Martin Fowler</cite>

Microservices architecture is a new buzzword in the recent years, but the idea behind it is not new at all. In fact, it's quire similar to the SOA pattern that was very popular a few years ago. Both microservices and SOA are about decomposing applications into smaller services for more efficient scaling and managing application life-cycles. They are not the same though, as explained in a [comprehensive post from Martin Fowler](http://martinfowler.com/articles/microservices.html#MicroservicesAndSoa). While SOA is a very general concept and can mean a lot of things, microservices architecture describes a particular way of building applications using very small services, each focusing on doing only one thing well.

There are two reasons behind microservices gaining popularity. First, as softwares become more and more complex, the traditional monolithic architecture no longer scopes with the needs for scalabilty and rapid development cycle. How microservices help with this we will see in the next section. Second, the success of large internet companies, [lead by Netflix](http://nginx.com/blog/microservices-at-netflix-architectural-best-practices), in implementing microservices architecture is a big motivation for others when consider switching over.


### How it works

The best way to explain microservices is to compare it to the old monolithic way of building applications, so let's have a quick recap.

In the traditional three-tier design, the server-side application takes the role of the middle layer, processing business logic and serving data from database tier to clients (web browers, mobile apps, internet of things, etc.). The application is written as a single, unified code base and everything run in the same process. Scaling is done by replicating the same monolithic application on multiple servers.

In microservices architecture, the monolithic is decomposed into multiple small, granular, **_independently deployable_** services. The fact that these services are independently deployable is very important, it enables some of microservices most important benefits. These services can be developed in parallel by different teams, using different technology stacks that are best suited for their purposes. Also, as they are independently deployed, they can be independently scaled. For example, a service that is CPU-heavy but doesn't need much memory can be scaled on servers equipped with powerful processor but lower memory. We can scale only the services we want, not all of them.

<p></p>
<p align="center">
	<img src="{{ site.BASE_PATH }}/assets/media/scale_cube.png" alt="scale cube" style="max-height: 250px"> <br/>
	<span class="img-caption">The Scale Cube &mdash; from the book <a href="http://theartofscalability.com">The Art of Scaling </a></span>
</p>
<p></p>

If the services are so independent and isolated, how should we share code between them? Well, this is a question of finding the balance point. While sharing code between services allows reusing existing functionalities and keeping the DRY principle, it also increases the coupling of the services. One solution is to share only the technical libraries, and the common functionalities can be made into stand-alone services that other services can call to. That leads us to the next thing, communication between services.

Communication between these microservices can be done in two main ways, HTTP and message queue ([Azure Service Bus](http://azure.microsoft.com/en-us/services/service-bus), [RabbitMQ](https://www.rabbitmq.com), [Apache Kafka](http://kafka.apache.org), etc.). Basically, HTTP is direct communication and should be used when you want an immediate response from the other service. On the other hand, the publish/subscribe mechanism of message queue is more "fire and forget" way.

Finally, as the services are very granular, client applications usually need to interact with multiple services to get the data they need. To allow changes in the services without affecting the clients, an [API Gateway](http://microservices.io/patterns/apigateway.html) is used. The API Gateway is an abstract layer that hides away all the microservices, leaving a single endpoint for clients to communicate. Requests coming to the gateway will be proxied/routed to the appropriate services. The gateway can also helps us to easily monitor the usage of the services.

<p></p>
<div class="row">
	<div class="col-md-6" align="center">
		<img src="{{ site.BASE_PATH }}/assets/media/monolithic_architecture_diagram.png" alt="monolithic architecture" style="max-height: 400px"><br/>
		<span class="img-caption" style="margin-left: -25px">Monolithic Architecture</span>
	</div>
	<div class="col-md-6" align="center">
		<img src="{{ site.BASE_PATH }}/assets/media/microservices_architecture_diagram.png" alt="monolithic architecture" style="max-height: 400px"><br/>
		<span class="img-caption" style="margin-left: -25px">Microservices Architecture</span>
	</div>
</div>

### The benefits

While the old monolithic architecture had worked well in the past, in the current world where applications need to deploy new features very often and need to be always-on, it's simply out of date. A change in a small part requires testing, re-buildin and re-deploying the entire application. And since everything run in the same process, an unhandled exception can bring down the whole monolithic system.

Microservices architecture, on the other hand, is much more flexible and resilient.

* The services themselves are very simple, focusing on doing only one thing well so they're easier to test and ensure a higher quality. 

* Each service can be built with the best suited technologies and tools, allowing [polyglot persistence](http://martinfowler.com/bliki/PolyglotPersistence.html) and such. You don't have to be stuck with an early choice of technology for the rest of the project. 

* Multiple developers and teams can deliver independently under this architecture. This is great for continuous delivery, allowing frequent releases while keeping the rest of the system stable. 

* In case a service goes down, it will only affect the parts that directly depend on it (if there are such parts). The other parts will continue to function well.


### Things you should look out for

Same as every other patterns and architectures, the microservices architecture is not a silver-bullet to every problems. While it solves a lot of problems of the old monolithic applications, it also introduces new problems that we need to consider.

With a lot of moving parts, microservices are on a different level of complexity compared to monolithic architecture. Significant DevOps skill is required to deploy and maintain a microservices application in production. While the monolithic application can be deployed into a small application servers cluster, each service in microservices requires it own cluster for failover and resilience. Adding load balancers and messaging layer for these clusters is not trivial work either. Strong automation release scripting skill is required to be able to leverage the continuous delivery benefit.

Microservices systems are distributed by nature, and distributed systems are difficult to build. A simple method call before could be now a remote procedure call, REST or asynchronous message. Developers now need to think more about problems like network latency between services, fault tolerance, versioning, etc. While these properties are always good to have in the system, they surely will take more effort to build.

And while the services are easier to test by themselves, end-to-end tests are more difficult. As the flow of code is complex, it can be difficult to figure out where in the chain that something goes wrong.

### Conclusions

Microservices architecture is a very promising way for designing and building highly scalable applications in an agile way. While we have seen the challenges in implementing microservices system, in my opinions most of them will be solved in the near future as the architecture gains popularity and more tools and frameworks are built to support it. Currently I'm looking into creating an internal project for training purpose, and I think it can be a perfect opportunity to try out the microservices architecture since we don't have to worry too much about the difficulties in production and such. I will write another post about the actual result after we have tried it.










