Debugging with an Integrated Development Environment (IDE)
===============================================================================

IMPORTANT: One of the most common sources of trouble that 
students encounter comes from poor file organization. Create a 
folder that will contain each of the labs and projects we will do this 
semester; then, when a lab or project is assigned, create a new 
folder in that master folder to hold all of the code for that project. 
Feel free to copy from previous labs or projects but never update 
code that works for an earlier lab or project so that it will work with 
the current one. You must always be able to back out to an earlier 
lab and have confidence that it will still work.

Assembly code
----------------

>>> $include (c8051f020.inc) 
>>>  
>>>         dseg at 30h 
>>> str_d:  ds      10h             ; reserve 16 bytes 
>>>  
>>>         iseg at 80h 
>>> str_i:  ds      10h             ; reserve 16 bytes 
>>> stack:  ds      70h             ; reserve the rest for 
>>> stack 
>>>  
>>>         xseg 
>>> str_x:  ds      10h             ; reserve 16 bytes 
>>>  
>>>         bseg 
>>> flag:   dbit    1               ; reserve 1 bit for flag 
>>>  
>>>         cseg 
>>>         mov     wdtcn,#DEh      ; Disable watchdog 
>>>         mov     wdtcn,#ADh 
>>>         mov     r0,#255 
>>> clrall: mov     @r0,#0          ; clear all internal ram 
>>>         djnz    r0,clrall 
>>>         setb    flag            ; set flag bit 
>>>         mov     sp,#stack-1     ; initialize stack 
>>>         mov     dptr,#str_x     ; point dptr at str_x 
>>>         mov     r0,#str_d       ; point r0 at str_d 
>>>         mov     r1,#str_i       ; point r1 at str_i 
>>>         mov     r6,#10          ; copy all the bytes 
>>>         mov     r7,#str_c-pc_rel; pc relative offset to str_c 
>>> loop1:  mov     a,r7            ; offset to first (next) byte 
>>>         movc    a,@a+pc         ; actually get the byte 
>>> pc_rel: mov     @r0,a           ; store in str_d 
>>>         mov     @r1,a           ; store in str_i 
>>>         movx    @dptr,a         ; store in str_x 
>>>         inc     r0 
>>>         inc     dptr            ; increment pointers 
>>>         inc     r7 
>>>         djnz    r6,loop1        ; loop 16 times 
>>> loop2:  sjmp    loop2           ; wait forever 
>>>  
>>> str_c:  db "Hello, Students", 0 
>>>         end 

>>> import pyvisa
>>> rm = pyvisa.ResourceManager()
>>> rm.list_resources()
>>> laser = rm.open_resource('GPIB0::20::INSTR')
>>> print("Equipment ID: ",laser.query('*IDN?'))