---
title: Forking, not just for dinner
date: 12/04/2016


Multi-process code is not something I have much experience with in general.  A lot of what I write is single threaded 
web code which is used behind a multi-threaded web server.

Recent work I've been doing has required that I brush up on multi-process stuff, like ...

Forking
---------

Forking in ruby is as simple as this:

    Process.fork { # do something in another process }
    
 Forking copies the current processes memory space, so inter-process communication is also very simple.
    
    read, write = IO.pipe
    pid = Process.fork do
      write.close
      write.puts "I am your child process" #send message from child to parent
      write.close
    end
    
    write.close  
    Process.wait(pid)
    puts read.gets
    read.close
    => 'I am your child process'
     
Spawn
-----

Spawn also creates a new process, but is more like executing a new program.
 
    pid = Process.spawn('some_program')
    
 Spawn technically operates in a sub-shell of the current command shell.   So all strengths and limitations of the 
 command shell are present when 'spawning' a new process.
    
Inter-process communication is still relatively simple.
    
    read, write = IO.pipe
    pid = Process.spawn('hello_world.rb', :out=>write) #presumably writes 'Hello World' to stdout
    write.close
    Process.wait(pid)
    puts read.gets
    => 'Hello World'
     
