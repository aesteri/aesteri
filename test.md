Computer Modeling Final Report
=============

**Contributors** Team 4: Christine Kim, Minseo Kwak, Minjae Kang

Homework 1: Design your own cyber system
-------

The process to getting the vehicle drive under 2 minutes and 40 seconds was a journey. We ended up altering the design.xml, CC.cpp, and LK.cpp in order to alter the period, deadline and execution time of Cruise Control (CC) and Lane Keeping (LK). 

In our initial attempts to make the vehicle travel past the target lap time, we configured the CC period and deadline in various ways. After playing around with the settings of CC and reaching a conclusion that the current speed was not ideal, we decided to alter the base speed of CC to 60. With configurations to the period and deadline, the vehicle was able to achieve a lap time of 3:23 seconds. With mishaps along the way as such as when we found out that if you increase the period of CC too much, then it could hinder the lap time of the vehicle.

At a certain point, we decided to focus on the interrogating the proportional gain component of PID, experimenting with the LK configurations and gradually increasing the proportional gain. We gained a new significant time by discovering the proportional gain's dependence on the road angle relative to the car $(\(\dot{\theta} = - \theta \cdot \alpha\))$. From this point on, we diverted our attention to figuring out what value of $\theta$ would set the course right for our cyber system. 

After increasing the speed again and altering  $\theta$ and  $\alpha$, we saw success in the configurations of _____, finally reaching a record lap time of ____.

Homework 2: Implementing Logger Functionality
-------

*CASE I: Vehicle does NOT move* 

In order to properly log the data in cases the vehicle is not able to move, a logging function was implemented to Logger to account for the tasks relating to vehicle movement (e.g. CC, LK)--reading and writing data. 

Below is the code for the function:

```
void Logger::team4_task_read_write_logger(std::string task_name) {
    std::ofstream log_output;
    log_output.open(utils::cpsim_path + "/Log/team4_read_write.log", std::ios::app);
    log_output.write(task_name.c_str(), task_name.size());
}
```

To develop the functionalities of this function, Logger::team4_task_read_write_logger is called in "Job.cpp" whenever a task is written and read. 

Below is an example:

```

```

Proceeding the calling of the function, we continue to log the findings in a log file named "team4_read_write.log".

Below is an example of the log:

```
10 READ LK TARGET_SPEED
10 WRITE LK ACCEL_VALUE
```

*CASE II: Stationary Vehicle & Empty Log File* 

In order to properly log the data in cases the vehicle is not able to move and we see not logging of vehicle movement tasks, a logging function was implemented to Logger to account for the schedule of the real cyber system.

Below is the code for the function:

```
void Logger::team4_real_cyber_schedule_logger(long long time, int job_id, std::string even_type){
    std::ofstream log_output;
    log_output.open(utils::cpsim_path + "/Log/team4_schedule.log", std::ios::app);
    log_output.write(time +  );
}   
```

To develop the functionalities of this function, Logger::team4_real_cyber_schedule_logger is called in "Executor.cpp" whenever a job is released, finished, started, or encountered a deadline miss.

Below is an example:

```

```

Proceeding the calling of the function, we continue to log the findings in a log file named "team4_schedule.log".

Below is an example of the log:

```
0 J11 RELEASED
0 J21 RELEASED
0 J31 RELEASED
0 J11 STARTED
10 J11 FINISHED
10 J21 STARTED
20 J12 RELEASED
```
