## **Banker's Algorithm Implementation**

The simulation of the Banker's Algorithm is founded on the principles of resource allocation using Python to prevent deadlocks in operating systems. This simulation encompasses a multi-threaded implementation aimed at acknowledging race conditions, thereby creating a more authentic and challenging environment. Through the utilization of locks and thread safety mechanisms, the simulation effectively handles resource requests originating from various processes concurrently to demonstrate the proficiency of the Banker algorithm and resource management comprehensively.

Project Overview and Implementation Guidelines:
The initial section of the project involves the implementation of multiple classes and functions devised to emulate the Banker algorithm and facilitate concurrency management. These classes and functions include:

1. Process Class: Responsible for representing a process, this class incorporates attributes for the maximum requisite resources, allocated resources, and the remaining required resources. Each process is equipped with a lock to ensure the effective management of thread safety.
class Process: def init(self, id, max_resources, allocated_resources): 
2. Resource Class: This class is responsible for managing the resources within the system, encompassing features that track both total resources and available resources, along with implementing a thread safety management lock.
class Resource: def init(self, total_resources): 
3. is_safe_state method: Its primary function is to determine the system's safety status by analyzing potential process sequences for deadlock avoidance. 
def is_safe_state(processes, available_resources): 
4. request_resources method: Moreover, this function oversees the allocation of resources from processes. Initially, resources are provisionally allocated, followed by a verification of the system's integrity. If the system is confirmed to be secure, the final resource allocation is executed; otherwise, the resource allocation request is declined.
def request_resources(process, request, processes, resources):
5. process_thread method: Furthermore, this function operates resource requests from processes through a separate thread, providing feedback on the request outcome. A success message is recommended for successful allocation:
Process process.id request granted. Safe sequence: sequence. 
and a failure message for unsuccessful allocation:
Process process.id request denied. System would be in an unsafe state. 
def process_thread(process, request, processes, resources): 
6. race_condition_monitor method: It continuously monitors the system to identify instances of resource over-allocation, ensuring the system's integrity and preventing potential resource conflicts.
def race_condition_monitor(processes, resources): 
7. display_state method: Additionally, it provides real-time updates on the system's status, detailing the available resources and the status of each process.
def display_state(processes, available_resources): 

The initial input should define the resources and processes, adhering to the specified format for accurate processing. 
total_resources = [10, 5, 7] 
resources = Resource(total_resources) 
processes = [ 
Process(0, [7, 5, 3], [0, 1, 0]), 
Process(1, [3, 2, 2], [2, 0, 0]), 
Process(2, [9, 0, 2], [3, 0, 2]), 
Process(3, [2, 2, 2], [2, 1, 1]), 
Process(4, [4, 3, 3], [0, 0, 2]) ]

Input Guidelines:
- The first line should include the total number of processes.
- The second line should list the required resources for each process, separated by spaces.

Example 1:
Available Resources: [3, 3, 5] 
Processes: 
Process 0: Max: [7, 5, 3], Allocated: [0, 1, 0], Need: [7, 4, 3] 
Process 1: Max: [3, 2, 2], Allocated: [3, 0, 2], Need: [0, 2, 0] 
Process 2: Max: [9, 0, 2], Allocated: [3, 0, 2], Need: [6, 0, 0] 
Process 3: Max: [2, 2, 2], Allocated: [2, 1, 1], Need: [0, 1, 1] 
Process 4: Max: [4, 3, 3], Allocated: [0, 0, 2], Need: [4, 3, 1] 

Input:
Enter process ID to request resources: 1 
Enter resource request (space-separated): 1 0 2

Output:
Process 1 request granted. Safe sequence: [1, 0, 3, 4, 2]

Example 2:
Available Resources: [3, 3, 5] 
Processes: 
Process 0: Max: [7, 5, 3], Allocated: [0, 1, 0], Need: [7, 4, 3] 
Process 1: Max: [3, 2, 2], Allocated: [2, 0, 0], Need: [1, 2, 2] 
Process 2: Max: [9, 0, 2], Allocated: [3, 0, 2], Need: [6, 0, 0] 
Process 3: Max: [2, 2, 2], Allocated: [2, 1, 1], Need: [0, 1, 1] 
Process 4: Max: [4, 3, 3], Allocated: [0, 0, 2], Need: [4, 3, 1] 

Input:
Enter process ID to request resources: 2 
Enter resource request (space-separated): 6 0 0 

Output:
Process 2 request denied. System would be in an unsafe state.

The second part of the project involves simulating resources that are periodically added to the system to simulate real -time resource change, and the classes and functions are as follows:
1. The DynamicResource class inherits from the Resource class and adds the ability to add resources to this dynamic class. This class helps manage dynamic resources and add new resources to the system over time:
class DynamicResource(Resource): def __init__(self, total_resources)
2. add_resources function is used in the DynamicResource class to add new resources to the system:
class DynamicResource(Resource): def add_resources(self, additional_resources)
3. The dynamic_resource_changer function continuously adds new resources to the system to simulate dynamic resource management. New sources are randomly produced and then added to system resources:
def dynamic_resource_changer(resource, interval)
Example to add a new source at the output of the application:
Resources added: [1, 2, 0]
New total resources: [11, 7, 7]
New available resources: [3, 2, 3]

The third part of the project involves simulating resource requests parallel and analyzing them for system safety. This section involves implementing a multi -test test to submit resource requests from different processes simultaneously and use the banking algorithm to check system safety. This helps simulate the actual behavior of operating systems in which different processes request resources simultaneously and the system must ensure the safety of resources allocation.
