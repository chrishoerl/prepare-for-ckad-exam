# Certified Kubernetes Application Developer Exam (CKAD)

## How I prepared for it in November 2022

### My situation:
* 3 years of professional experience with K8s
* 18 years of professional experience in Linux

### Kubernetes Version
My exam was performed on K8s v1.25

### Material / Courses
* **Kubernetes Documentation**: it is a valuable pool of information and its search function also finds bash commands such as: "busybox while true"
As it is the most important resource during the exam, I forced myself to solve my problems with tips and examples from the official docs.

https://kubernetes.io/docs/

* **Udemy Course**: "Certified Kubernetes Administrator (CKA) with Practice Tests"

https://www.udemy.com/share/1013BQ/

* **killer.sh** is now included free for all exam attendees on enrollment process

https://killer.sh/cka

### Timeline
* started with Udemy course and completed all the videos (14.5 hours) and KodeKloud practice tests (~8-12 hours)
* then repeated some Udemy videos I was not so self-confident with
* then repeated some KodeKloud practice tests for the 2nd time
* repeated the Lightning Labs and the Mock Exams on KodeKloud once more to become faster

* scheduled the date for my exam (1 weeks in advance on a Sunday afternoon)
* again repeated some Udemy videos which I had not fully understood

### In the last week before the exam:
* **Monday**: repeated some Udemy lectures and KodeKloud Lab exercises I was not so confident with
* **Tuesday**: picked a few lab exercises on KodeKloud and tested them on my own local K8s cluster
* **Wednesday**: did my first of two killer.sh sessions and performed "ok" (79/112 points)
* **Thursday**: reworked all Questions and Answers of killer.sh (without timer) to understand each solution
* **Friday**: started my 2nd killer.sh session and performed well properly (104/112 points) - I already knew the solutions from first run but this time I did it for a better feeling of time management (with the timer of 2 hours)
* **Saturday**: reworked the few questions from killer.sh which I still did wrong
* **Sunday**: summit day.... erm... exam day. - Had a good feeling afterwards.
* **Monday**: Got my result: Passed! 78% of 100 points.

* after all the preparation and finally the exam took 3 weeks

### Tools

I use:
* kubectl autocompletion with the alias of "k"

I do not use:
* terminal managers such as tmux, just a plain single terminal

### Favorite K8s shortcuts

This is a list of my favorite and most-used links and examples for creating K8s objects.

* Create a container to test other pods and services:
```
kubectl run curl --image=radial/busyboxplus:curl -i --tty
```

* Run a command in a shell:
```
command: ["/bin/sh"]
args: ["-c", "while true; do echo hello; sleep 10;done"]
```

* Create a pod in a 1-liner
```
kubectl run mypod --image=nginx --dry-run=client -o yaml > mypod.yml -- sh -c echo "hello"
kubectl -n default apply -f mypod.yml
kubectl -n default get po
```

* API resources 
```
kubectl api-resources
kubectl api-resources --namespaced=true
kubectl api-resources --namespaced=false
```

* Explain K8s objects

If you want to know the object structure of pods:
```
kubectl explain pods --recursive  | wc -l
996 #note this number!

kubectl explain pods --recursive  | grep image -b996

# this will color-mark the object in the given structure you were looking for.
# This helps to build structured commands for jsonpath! 
```

### Favorite links

* kubectl Cheat Sheet

  https://kubernetes.io/docs/reference/kubectl/cheatsheet/

* Configure a Pod to Use a Volume for Storage

  https://kubernetes.io/docs/tasks/configure-pod-container/configure-volume-storage/

* Configure a Pod to Use a PersistentVolume for Storage

  https://kubernetes.io/docs/tasks/configure-pod-container/configure-persistent-volume-storage/

* Network Policy

  https://kubernetes.io/docs/concepts/services-networking/network-policies/#networkpolicy-resource

* Security Context

  https://kubernetes.io/docs/tasks/configure-pod-container/security-context/


### Environment
I set up my own local K8s cluster on a notebook

Tutorial: https://github.com/chrishoerl/k8s-play

### My desk for the exam day
* notebook with lid closed (it plays audio in case the proctor wants to say something)
* big 21:9 wide external screen
* Webcam Logitech C920 HD Pro on top of my screen
* USB keyboard
* mouse
* 1 bottle of water
* door locked for no one to come in and disturb me
* leave your mobile phone outside the room

### Room tip:

If you want to do the exam in a room you are not so familiar with, make sure to prepare the room fitting your needs.
* light
* window

### Comment on the exam environment ###

The proctoring company PSI has a mandatory "PSI Secure Browser" which every test participant must use.
Unfortunately the performance of this special browser and the remote linux desktop it is connected with is really slow.

* slow typing in terminal windows
* slow scrolling in the remote firefox browser to read k8s documentation
* also copying and pasting text works only with special key combination of CTRL+C (copy) and CTRL-Shift-v (paste) in the terminal

This slow behaviour took me about 5-10 minutes of my testing time to get used to it.
