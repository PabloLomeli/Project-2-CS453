# Overview

In this project, we will create a thread-safe version of an existing list library. We will then test it using a provided solution to the producers-consumers problem.

You will create the ThreadsafeBoundedList.c file in the wrapper-library subfolder to complete the implementation of the thread-safe list library.

To have a clean compile, be in the root directory and use the following command: make clean 
Then: make all

To use this program use the following format on the command line afer compiling: ./pc <poolsize> <#items/producer> <#producers> <#consumers> <sleep interval(microsecs)>

# Student Explanation

So after creating ThreadsafeBoundedList.c, I was able to fill in the blanks for all methods. I did not implement removeNode() though due to the professor saying it isn't necessary to implement. There are a few methods that are not really ever used to be honest but I decided to fill in the blanks anyways on those. The main problem when doing this project was just understanding the concept of producers/consumers, single monitor queue, and how that tied in with the pc.c program given. At first I implemented ThreadsafeBoundedList.c to just produce and consume without checking condition variables but having mutual exclusion. This made pc.c produce and consume but was not taking into account if there was stuff to produce or things to consume, it just did it if it was available and if it wasn't then CPU utilization was wasted. After implementing a way for consumer threads to "wait" and taking into account condition variables, I was able to ensure that producer threads always woke up consumer threads when an insert happened, and a consumer thread always woke up a producer thread when a removal happened. Another thing that consumer threads do is wait due to lists being emptied before they can be populated again. After testing with a single command with ./pc x x x x and making sure to get the right command arguments and using VERBOSE debug value, I went ahead and tested with ./test-pc.sh and everything seems to work.


## Submission
Create a private repository on github and give access permission to this account: jidongbsu (or using the email address: jidongxiao@boisestate.edu). You can use one repository for all 3 projects in this course, so that you only need to grant access permission to Jidong once.

Due Date:  October 27th, 2020.

## Grading Rubric

- [10 pts] Compiling
  - Each compiler warning will result in a 3 point deduction.
  - You are not allowed to suppress warnings
- [80 pts] Functional Requirements: single queue monitor
- [10 pts] Documentation: README.md file
