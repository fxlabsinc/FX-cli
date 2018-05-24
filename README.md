# FX-cli

Use the FX command-line tool, FX-cli, to run Fx jobs from a developer machine. Using FX-cli, you can execute jobs and override values for region, tags, environments and give a list of suite names to run.

FX-cli improves productivity when you're writing new tests and constantly making changes to the test suite files without actually check-in to version-control systems. Once the jobs are stable you can then check-in the new files and make them part of the larger job scopes.

## Before you begin
Use a version of FX-cli that is the same version as your FX-Cloud or FX-On-Premises. Using an older FX-cli with a newer server might produce errors.


## Install on MacOS
   > FX-cli requires Java 8 minimum. You can download it from [here](https://java.com/en/download/)
   
   Download FX-cli from [here](https://github.com/fxlabsinc/FX-cli/)
   
   Run FX-cli 
   ```
   ./Fx-cli.jar
   ```

## Install on Linux
   > FX-cli requires Java 8 minimum. You can download it from [here](https://java.com/en/download/)
   
   Download FX-cli from [here](https://github.com/fxlabsinc/FX-cli/)

   Run FX-cli 
   ```
   ./Fx-cli.jar
   ```

## Install on Windows
   > FX-cli requires Java 8 minimum. You can download it from [here](https://java.com/en/download/)
   
   Download FX-cli from [here](https://github.com/fxlabsinc/FX-cli/)

   Run FX-cli 
   ```
   java -jar Fx-cli.jar
   ```

## Documentation

   ### Run FX-cli 
   ```
   ./Fx-cli.jar
   ```
   or
   ```
   java -jar Fx-cli.jar
   ```
   
   ### This is what you see if the FX-cli comes up fine.
   ```
   $ ./FX-cli.jar
   Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=256m; support was removed in 8.0
    _______  __   _          _
   |  ___\ \/ /  | |    __ _| |__  ___
   | |_   \  /   | |   / _` | '_ \/ __|
   |  _|  /  \   | |__| (_| | |_) \__ \
   |_|   /_/\_\  |_____\__,_|_.__/|___/

   Reading credentials from fx.properties
   Welcome Admin!
   FX-cli >
   ```
   
   ### This is what you see if the FX-cli fails to start.
   ```
   $ ./FX-cli.jar
   Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=256m; support was removed in 8.0
    _______  __   _          _
   |  ___\ \/ /  | |    __ _| |__  ___
   | |_   \  /   | |   / _` | '_ \/ __|
   |  _|  /  \   | |__| (_| | |_) \__ \
   |_|   /_/\_\  |_____\__,_|_.__/|___/

   Reading credentials from fx.properties
   2018-05-23 16:45:51.948  WARN 30021 --- [           main] com.fxlabs.fxt.cli.FxCommands            : URI is not absolute
   Login failed!

   FX-CLI will try to read login credentials from the following locations
   fx.properties
   /opt/fx/fx.properties
   /var/fx/fx.properties
   C:\opt\fx\fx.properties
   ${user.home}/fx/fx.properties

   e.g. file content
   fx_url=https://cloud.fxlabs.io
   fx_username=me@company.com
   fx_password=mypassword
   ```
   
   ### fx.properties
   FX-cli requires a fx.properties file in one of these location. FX-cli uses this file to connect to the FX-Cloud (https://cloud.fxlabs.io) or FX-On-premises instance.
   
   #### fx.properties locations
   ```
   /opt/fx/fx.properties
   /var/fx/fx.properties
   C:\opt\fx\fx.properties
   ${user.home}/fx/fx.properties
   ```
   
   #### fx.properties content
   ```
   fx_url=https://cloud.fxlabs.io
   fx_username=me@company.com
   fx_password=mypassword
   ```
   
   ### FX-cli has 2 commands (run & gen).
   
   ### help command
   ```
   FX-cli > help
   AVAILABLE COMMANDS

   Built-In Commands
           clear: Clear the shell screen.
           exit, quit: Exit the shell.
           help: Display help about available commands.
           script: Read and execute commands from a file.
           stacktrace: Display the full stacktrace of the last error.

   Fx Commands
           gen: Auto generates quality and security coverage test-suites for Open API spec
           run: Executes job

   ```
   
   ### clear command (clears screen)
   ``` 
   FX-cli > clear 
   ```
   
   ### exit command (exits FX-cli)
   ```
   FX-cli > exit
   ```
   
   ### help command
   ```
   FX-cli > help
   AVAILABLE COMMANDS

   Built-In Commands
           clear: Clear the shell screen.
           exit, quit: Exit the shell.
           help: Display help about available commands.
           script: Read and execute commands from a file.
           stacktrace: Display the full stacktrace of the last error.

   Fx Commands
           gen: Auto generates quality and security coverage test-suites for Open API spec
           run: Executes job

   ```
   
   > help 'gen' command
   ```
   FX-cli > help gen


   NAME
      gen - Auto generates quality and security coverage test-suites for Open API spec

   SYNOPSYS
      gen [-h] string  [-d] string  [[-k] string]  [[-v] string]

   OPTIONS
      -h or --url  string
         OpenAPI URL e.g. http://ip/v2/api-docs or myapp-spec.json
         [Mandatory]
         [size must be between 1 and 2147483647]

      -d or --dir  string
         Stub generation directory e.g. C:\MyApp or /opt/MyAppTest or C:\MyApp\test-suites
         [Mandatory]

      -k or --auth-header-key  string
         Authorization header key e.g. 'Authorization'
         [Optional, default = ]

      -v or --auth-header-val  string
         Authorization header value e.g. 'my-passowrd'
         [Optional, default = ]

   ```
   
   > help 'run' command
   ```
   FX-cli > help run


   NAME
      run - Executes job

   SYNOPSYS
      run [-p] string  [[-d] string]  [[-j] string]  [[-r] string]  [[-t] string]  [[-e] string]  [[-s] string]

   OPTIONS
      -p or --project  string
         Project name e.g. org/project-name or FxLabs/Common
         [Mandatory]
         [size must be between 3 and 2147483647]

      -d or --dir  string
         Project directory path e.g. /opt/Project1 or C:/Project1
         [Optional, default = ]

      -j or --job  string
         Job name from Fxfile.yaml e.g. Stg or Dev etc
         [Optional, default = Default]

      -r or --region  string
         Override bot region for the job e.g. org/region or FxLabs/US_WEST_1
         [Optional, default = ]

      -t or --tags  string
         Override tags e.g. V1,V2
         [Optional, default = ]

      -e or --env  string
         Override env for the job e.g. Stg or Dev etc
         [Optional, default = ]

      -s or --suites  string
         Comma separated test-suite names
         [Optional, default = ]
   ```
   
   ##### run command examples
   > project value should match the project name on FX-Cloud UI and is mandatory e.g -p FXLabs/MyApp.
   > job value should match the job name in the FXfile.yaml. e.g. -j Default or -j Local etc.
   > suites is optional, you can use this property to run one or more test suites e.g. -s vault_params.negative_2
   > directory value should point to your test project e.g. -d /opt/My-Test
   ```
   run -p FXLabs/MyApp -j Local -s vault_params_negative_2 -d /opt/My-Test
   ```
   
   ##### gen command examples

## Demo

