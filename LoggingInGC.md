# Logging In GC

There are various ways to log messages from the GC and based on scaling critera.

For Stress and Simple Logging, uncomment the following lines in `gc.h`:

```c
//#define TRACE_GC
```

For simple logging, you'll need to also uncomment this line.

```c
//#define SIMPLE_DPRINTF
```

## Stress Logs

Stress Logging is the most efficient and scalable way for logging messages from the GC but does involve making use of the Stress Log Analyzer for consumption. The messages are flushed out from a memory mapped file and therefore, are binary and can't be viewed by a text editor. Messages are written out by ``dprintf`` calls.

Example configurations include:

```
export COMPlus_StressLogFilename=GCPerfSimStresslog.log
export COMPlus_LogLevel=9
export COMPlus_StressLog=1
export COMPlus_StressLogSize=10000000
export COMPlus_TotalStressLogSize=20
```

## Simple Log

Writes log messages as text directly to a file using ``dprintf`` and the specified level. 

Example configurations include:

```
export COMPlus_GCLogEnabled=1
export COMPlus_GCLogFileSize=100
export COMPlus_GCLogFile="C:\\Replace_Char_Custom\\Segments.log" 
export COMPLUS_StressLog=0
```

## Printfs

Simple but not cheap and we definitely don't want these in production. These messages will show up in the console.

```c
printf("Hello %d", num);
```
