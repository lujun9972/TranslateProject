[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Explaining Kubernetes in 10 minutes using an analogy)
[#]: via: (https://opensource.com/article/20/7/kubernetes-analogy)
[#]: author: (Satyajit Das https://opensource.com/users/satyajit-das)

Explaining Kubernetes in 10 minutes using an analogy
======
Having trouble understanding Kubernetes? Try this analogy of using a
rental house to explain how it works.
![Houses in a row][1]

The concepts behind the [Kubernetes][2] container orchestration system can be hard to understand. I created a simple analogy about renting out rooms in a house to help you learn how Kubernetes works.

### How to rent rooms in your house

Imagine you own a house with 10 rooms. You want to rent out three of the rooms through an online accommodation service. You have two choices: you can post ads and manage everything yourself, or you can hire someone to do it for you.

Because it's simpler for you, you decide to hire a rental agent to take care of these things. Your **contract** with the agent states:

  * At all times, **three rooms** should be available to rent to guests.
  * Each room will have **two beds**.
  * Every time a guest books, the keys need to be handed over at the right time.
  * Every time a guest leaves, the rooms have to be cleaned.
  * If there are too many booking requests (during a holiday season, for instance), then booking availability can increase from three to ten.



That's it! Your responsibilities are mostly over, although you can use a phone to contact the agent to check in from time to time.

### How to manage a rental property

The agent hires **employees** to take care of your requirements. Let's say there are three employees to manage three rooms: when room one is booked, employee one ensures it's in good condition, provides the keys, cleaning service, and so on.

The bed is the _most basic_ entity because it's the minimum requirement needed by a guest to spend a night.

The agent keeps all the information about employees, rooms, beds, bookings, and so on, in a **notebook**. The agent also keeps track of employee time off in order to allocate another employee to the room should one employee fall ill or goes on holiday. The agent uses the **phone** to reach employees as needed.

When a guest books a room online, the booking is redirected to one of the employees, who ensures the room is ready. The guest arrives, gets the keys, and sleeps in the bed at night. The room is cleaned afterwards, and the cycle repeats.

This all sounds very simple, but what has it got to do with Kubernetes?

### What Kubernetes has to do with this

The automation you achieved by hiring the agent who employs others is similar to what Kubernetes does with an application. Here's how it works.

Say you are an app developer instead of a rental-house owner. As the most basic entity in a rental room is the bed, your **application** (the most basic entity that serves your user's needs) runs inside a **container**. The application's "room" is called a **pod**, which is where your application runs.

![Developer, Container, and Pod][3]

(Satyajit Das, [CC BY-SA 4.0][4])

A **node** or **worker node** is essentially a machine in which a pod runs.

The agent's employees ensure a guest room is fully functional. In Kubernetes, you don't have an employee but something called a **kubelet**. A **kubelet** is an agent inside a node that ensures the pods running inside that node are healthy.

![Kubernetes node and kubelet][5]

(Satyajit Das, [CC BY-SA 4.0][4])

The rental agent corresponds to two things in Kubernetes: **kube-scheduler** and **kube-controller manager**. Just as the agent decides which room should be assigned to which employee, the kube-scheduler decides which pod runs in which node, based on what resource is available and what its requirements are. Remember, a node is a machine, and the pod runs inside a node. Like the agent deciding what to do when an employee is off work, the kube-controller manager decides what to do when a node goes down or the machine stops working for any reason.

The agent's notebook, where all the details are recorded about how many rooms to rent, how many beds are available, which employee is doing what, and so on, corresponds to the **etcd** data storage. That's where configuration data is stored, for example, if you need three pods to be up all the time.

![Scheduler, Controller Manager, etcd][6]

(Satyajit Das, [CC BY-SA 4.0][4])

The main and worker nodes in Kubernetes operate like the phones that the agent and the employees use to communicate. The main **api-server** is like the agent's phone, while each worker node's **kube-proxy** is the like the employees' phones.

![API server connecting components together][7]

(Satyajit Das, [CC BY-SA 4.0][4])

The api-server, etcd, kube-controller manager, and kube-scheduler comprise a sort of control center for this Kubernetes instance.

![Kubernetes Master][8]

(Satyajit Das, [CC BY-SA 4.0][4])

### Deployment

The contract between you (the house owner) and the agent is equivalent to a **deployment** in Kubernetes. A deployment includes your set of requirements, such as how many pods need to be running, what resources (CPU, for example) you need, and so on. Kubernetes ensures these requirements are satisfied without manual intervention.

![Kube-proxy and deployment][9]

(Satyajit Das, [CC BY-SA 4.0][4])

Remember about the extra clause in the agreement about what to do if too many guests book? This is equivalent to **autoscaling** in Kubernetes. That means Kubernetes can scale your services, giving you more pods as your application users increase, just as you can make more rooms available if more guests are trying to book. Just as you can't extend your bookings beyond 10 rooms, you probably need to add a cap on autoscaling, because you can't arbitrarily continue to increase pods without running out of money for hosting your servers.

### Learn more

This brief analogy about how Kubernetes works is a good place for beginners to start. To learn more, you might also enjoy my [Kubernetes videos][10].

* * *

_This article is based on [Kubernetes: The Simplest Introduction for a Non-Programmer][11], originally published on the Tennexas blog, and is reused with permission._

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/7/kubernetes-analogy

作者：[Satyajit Das][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/satyajit-das
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/house_home_colors_live_building.jpg?itok=HLpsIfIL (Houses in a row)
[2]: https://opensource.com/resources/what-is-kubernetes
[3]: https://opensource.com/sites/default/files/uploads/developer-container-pod.png (Developer, Container, and Pod)
[4]: https://creativecommons.org/licenses/by-sa/4.0/
[5]: https://opensource.com/sites/default/files/uploads/kubernetesnode-kubelet.png (Kubernetes node and kubelet)
[6]: https://opensource.com/sites/default/files/uploads/scheduler-controllermanager-etcd.png (Scheduler, Controller Manager, etcd)
[7]: https://opensource.com/sites/default/files/uploads/api-server.png (API server connecting components together)
[8]: https://opensource.com/sites/default/files/uploads/kubernetesmaster.png (Kubernetes Master)
[9]: https://opensource.com/sites/default/files/uploads/kubeproxy.png (Kube-proxy and deployment)
[10]: https://www.youtube.com/watch?v=-wr_lNd6y84&list=PLBZT_qt7qHRQDQoFzfDRy6Zj77fPuyx80
[11]: https://tennexas.com/kubernetes-the-simplest-introduction/
