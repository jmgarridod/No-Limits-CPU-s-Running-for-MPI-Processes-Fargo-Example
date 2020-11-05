# No-Limits-CPU-Running-for-MPI-Processes-Fargo-Example

If you have many CPU (8,16 or more) and MPI limits the number you want to use. Calling a short .txt file you can use  unlimits CPU.

I have 8 CPU in my notebook, and I want run Fargo-ADSG using "mpirun" with 6 CPU but ..

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

write the number of CPU limits that you want use. you can know the number of CPU with


```sh
lscpu
```

Finally, call "--hostfile" and then /../hostfile.txt. (I suggest save the file in the same folder than fargo)
```sh
[name_user@name_computer FargoADSG]$ mpirun -np 6 --hostfile /directory/of/hostfile/hostfile.txt ./fargo -m /directory/of/the/par/file/adsg.par 
```

#### Make sure don't use the maximum number of CPUs, left 1 or 2 free for another tasks in your pc.

