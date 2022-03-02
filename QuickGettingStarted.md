# Quick Steps to Get Started With GC Development

## Building
1. Clone the runtime repo: ``git clone http://github.com/dotnet/runtime``.
2. __Building On Windows__ 
   1. To build the clr and libs on Windows: ``build.cmd -subset clr+libs -configuration [checked/debug/release]``
      1. ``debug``: No optimizations but assertions. 
      2. ``checked``: Optimizations and assertions.
      3. ``release``: Optimizations but no assertions.
3. __Building on Linux__
   1. __Installing WSL__
      1. Open up a new Powershell Window in Admin mode and type: ``wsl --install -d Ubuntu-20.04``
      2. Wait for installation to complete. NOTE: You'll need at least 20 GB of space for the OS.
      3. Once installed, type ``ubuntu`` to launch Ubuntu.
      4. Setup account accordingly.
      5. Type the following to get the latest updates: ``sudo apt update``.
      6. Install dependencies: ``sudo apt-get install -y cmake llvm-9 clang-9 \ build-essential python curl git lldb-6.0 liblldb-6.0-dev \ libunwind8 libunwind8-dev gettext libicu-dev liblttng-ust-dev \ libssl-dev libnuma-dev libkrb5-dev zlib1g-dev ninja-build``
      7. Build the runtime: ``./build.sh -configuration debug -subset clr``

## Testing a Modified Runtime With A Simple Console App
1. Create a new console app: ``dotnet new console``
2. Publish the console app as a self-contained app for Windows: ``dotnet publish -r win-x64 --self-contained``
3. Copy the updated version of the clr to the appropriate directory:
   1. ``cd bin\Debug\netx.0\win-x64\publish``
   2. ``xcopy /s/y {Directory where the CLR binaries are built to}\* .``
4. Run the Console App with the modified runtime: ``HelloWorld.exe``