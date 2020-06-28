# No-Limits-Threads-Running-for-MPI-Processes-Fargo-Example

If you have many thread (8,16 or more) and MPI limits the number you want to use. Calling a short .txt file you can use  unlimits threads.

I have 8 treads in my notebook, and I want run Fargo-ADSG using "mpirun" with 6 threads but ..

Error menssage:

```sh
[name_user@name_computer FargoADSG]$ mpirun -np 6 ./fargo -m /directory/of/the/par/file/adsg.par 
--------------------------------------------------------------------------
There are not enough slots available in the system to satisfy the 6
slots that were requested by the application:

  ./fargo

Either request fewer slots for your application, or make more slots
available for use.
```

The solution is create a "hostfile.txt" and call it. Is a short 1 line .txt file.

hostfile.txt:
```sh
localhost slots=7
```

write the numer of thread limits that you want use. 
