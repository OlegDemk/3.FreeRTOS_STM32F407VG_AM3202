# 3.FreeRTOS_STM32F407VG_AM3202

AM2302 using for measure T and H. 

Measure makes every 3 secind in task: Start_AM2302.

For read data from AM2302 nead create MICROSECONDS DELAY. For do that was used Tim10 with settings: Closk = 168Mz, Prescaler = 168-1, Counter = 10-1. It gives generate 10us period of time. Function delay_us gets value us BUT DOESEN"T les than 10. 

delay_us functions algorithms:
1. Function gets how meny us nead delay, and convert it in timer tics().   tim_val = us/10;
2. It is global variable. (tim_val)
4. Inside HAL_TIM_PeriodElapsedCallback Timer10 decrement value until tim_val == 0.    tim_val = tim_val - 1;
5. Function delay_us waits when tim_val = 0.  while(tim_val != 0)
6. Out

In timmer_handler(HAL_TIM_PeriodElapsedCallback) decrement "tim_val" from start value to 0.

Data transmitting over Virtual COM port. 115200.
