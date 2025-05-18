# Series Queues with infinite capacity - Open Jackson Network

## Aim :
To find (a) average number of materials in the system (b) average number of materials in the each conveyor of (c) waiting time of each material in the system (d) waiting time of each material in each conveyor, if the arrival  of materials follow Poisson process with the mean interval time 12 seconds, service time of  lathe machine in series follow exponential distribution  with service time  1 second, 1.5 seconds and 1.3 seconds respectively and average service time of robot is 7 seconds.

## Software required :
Visual components and Python

## Theory

![image](https://user-images.githubusercontent.com/103921593/203239736-7b81f599-71a8-4ae7-b63e-5d98acd9ea54.png)


## Procedure :

![image](https://user-images.githubusercontent.com/103921593/203239789-bc870dce-6727-487b-a0e2-4fc3f5114889.png)


## Experiment:
![Summa](image.png)
![Summatha](image-1.png)

## Program
```python
import math

# Getting Inputs
ArrivalTime = float(input("Enter the mean inter arrival time of objects from Feeder (in secs): "))
ServiceTime1 = float(input("Enter the mean inter service time of Lathe Machine 1 (in secs): "))
ServiceTime2 = float(input("Enter the mean inter service time of Lathe Machine 2 (in secs): "))
ServiceTime3 = float(input("Enter the mean inter service time of Lathe Machine 3 (in secs): "))
RobotTime = float(input("Enter the Additional time taken for the Robot (in secs): "))

# Calculating Lambda and Mu for each server
Lambda = 1 / ArrivalTime
Mu1 = 1 / (ServiceTime1 + RobotTime)
Mu2 = 1 / (ServiceTime2 + RobotTime)
Mu3 = 1 / (ServiceTime3 + RobotTime)

print("Series Queues with Infinite Capacity - Open Jackson Network")
print("The mean arrival rate per second               : %0.2f" % Lambda)
print("The mean service rate per second of Lathe 1    : %0.2f" % Mu1)
print("The mean service rate per second of Lathe 2    : %0.2f" % Mu2)
print("The mean service rate per second of Lathe 3    : %0.2f" % Mu3)

# Check for stability condition
if (Lambda < Mu1) and (Lambda < Mu2) and (Lambda < Mu3):
    # Calculating performance metrics for each server
    Ls1 = Lambda / (Mu1 - Lambda)
    Ls2 = Lambda / (Mu2 - Lambda)
    Ls3 = Lambda / (Mu3 - Lambda)

    Ls = Ls1 + Ls2 + Ls3  # Total number in system

    Lq1 = Ls1 - Lambda / Mu1
    Lq2 = Ls2 - Lambda / Mu2
    Lq3 = Ls3 - Lambda / Mu3

    Wq1 = Lq1 / Lambda
    Wq2 = Lq2 / Lambda
    Wq3 = Lq3 / Lambda

    Ws = Ls / (3 * Lambda)

    # Output
    print("Average number of objects in the system S1     : %0.2f" % Ls1)
    print("Average number of objects in the system S2     : %0.2f" % Ls2)
    print("Average number of objects in the system S3     : %0.2f" % Ls3)
    print("Average number of objects in the overall system: %0.2f" % Ls)
    print("Average number of objects in the conveyor S1   : %0.2f" % Lq1)
    print("Average number of objects in the conveyor S2   : %0.2f" % Lq2)
    print("Average number of objects in the conveyor S3   : %0.2f" % Lq3)
    print("Average waiting time of an object in conveyor S1: %0.2f secs" % Wq1)
    print("Average waiting time of an object in conveyor S2: %0.2f secs" % Wq2)
    print("Average waiting time of an object in conveyor S3: %0.2f secs" % Wq3)
else:
    print("Warning! Objects Overflow will happen in the conveyor")

```

## Output
```
Series Queues with Infinite Capacity - Open Jackson Network

The mean arrival rate per second               : 0.08
The mean service rate per second of Lathe 1    : 0.12
The mean service rate per second of Lathe 2    : 0.11
The mean service rate per second of Lathe 3    : 0.11

Average number of objects in the system S1     : 0.67
Average number of objects in the system S2     : 0.85
Average number of objects in the system S3     : 0.78
Average number of objects in the overall system: 2.30
Average number of objects in the conveyor S1   : 0.01
Average number of objects in the conveyor S2   : 0.26
Average number of objects in the conveyor S3   : 0.22
Average waiting time of an object in conveyor S1: 0.13 secs
Average waiting time of an object in conveyor S2: 3.26 secs
Average waiting time of an object in conveyor S3: 2.74 secs

```
## Result

Thus the program is implemented and executed successfully.
