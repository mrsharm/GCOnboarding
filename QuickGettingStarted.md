# Quick Steps to Get Started With GC Development

## Building
1. Clone the runtime repo: ``git clone http://github.com/dotnet/runtime``.
2. To build the clr and libs on Windows: ``build.cmd -subset clr+libs -configuration [checked/debug/release]``
      1. ``debug``: No optimizations but assertions. 
      2. ``checked``: Optimizations and assertions.
      3. ``release``: Optimizations but no assertions.

## Testing a Modified Runtime With A Simple Console App
1. Create a new console app: ``dotnet new console``
2. Publish the console app as a self-contained app for Windows: ``dotnet publish -r win-x64 --self-contained``
3. Copy the updated version of the clr to the appropriate directory:
   1. ``cd bin\Debug\netx.0\win-x64\publish``
   2. ``xcopy /s/y {Directory where the CLR binaries are built to}\* .``
4. Run the Console App with the modified runtime: ``HelloWorld.exe``