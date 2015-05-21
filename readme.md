# Visual Studio Code Setup
## For ASP.NET 5 on Linux Ubuntu

1. Download and install **Visual Studio Code**

  - Instructions: https://code.visualstudio.com/Docs/setup
  - Under Home, create a folder called **VSCode**.
  - Extract downloaded zip file to this location
  - Create a link to launch Code from Terminal by typing `code .`
    ```
    sudo ln -s /home/parallels/VSCode/Code /usr/local/bin/code
    ```
  - Create a folder under Home called **Source**
    + Navigate to Source in Terminal and enter:  `code .`
    + VS Code will open at this location
    
2. Install **ASP.NET 5** on Mac OS X

  - Instructions: http://docs.asp.net/en/latest/getting-started/installing-on-linux.html
  - Install Homebrew if needed
    + ```ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"```
    + Install command line developer tools when prompted
  - Uninstall `kvm` if previously installed
  - Get homebrew `dnx` repo (tap)
    ```
    brew tap aspnet/dnx
    ``` 
  - To update `dnx` repo: untap then tap
  - Install DotNet Version Manager: `dnvm`
    ```
    brew install dnvm
    dnvm
    dnvm upgrade
    ```
  - If ```dnvm``` will not run enter: ```source dnvm.sh```
  
3. Run **console sample**
  - Create ConsoleApp folder
  - Go to the aspnet repo: https://github.com/aspnet/Home/tree/dev/samples/latest/ConsoleApp
  - Download: project.json, program.cs
  - Restore packages: `dnu restore`
  - Run the app: `dnx . run`
  
4. Run ** web sample**
  - Create WebApp folder
  - Go to the aspnet repo: https://github.com/aspnet/Home/tree/dev/samples/latest/HelloWeb
  - Download: project.json, startup.cs
  - Restore packages: `dnu restore`
  - Run the app: `dnx . kestrel`
  - Open a browser and go to: http://localhost:5004
  - Try stopping kestrel by pressing Enter
  - If it does not stop, open another terminal to kill the process:
    ```
    ps {To see a list of PIDS}
    kill -9 {PID #}
    ```

5. Scaffold an **ASP.NET Web API** app using **Yeoman**
  - If necessary install the node package manager: `npm`
    + Download: https://nodejs.org/download
  - Install Yeoman, the asp.net generator, grunt and bower:
  
    `sudo npm install -g yo grunt-cli generator-aspnet bower`
  - Go to parent folder in Terminal and run `yo aspnet`
    + Pick Web API Application, enter as name: HelloWebApi
  - Run `dnu restore`, then run as before
  - Open a browser and go to: http://localhost:5001/api/values
  - Press Enter to stop Kestrel, or kill as before
