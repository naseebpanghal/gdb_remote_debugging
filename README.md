Remote Debugging with gdbserver 
###############################

Two machines are required for this. One Target Machine where actually application will be running and another one is Client/Host machine where debugging commands will be performed.

Perform below steps for remote debugging.
1. Build application without debugging symbols(-g option).
2. Put application on Target Machine.
3. Run application with command 
   * $gdbserver 192.168.100.237:1234 <app name> <arguments if required>
   * NOTE: Here above 0.0.0.0 can be used if you want debugging from any machine.

4. Build application again with debugging symbols for client machine.
5. Run application with below command
   * $gdb <app name>
   * $(gdb) target remote 192.168.100.197:1234
   * $(gdb) b <function name>
   * $continue (run/r command doesn't work here)

6. All other things are similar to normal gdb.

NOTE:
In above example,
* 192.168.100.237: Client Machine IP
* 192.168.100.197: Target Machine IP

For Cross-debugging, refer below link:
https://www.linux.com/news/remote-cross-target-debugging-gdb-and-gdbserver
