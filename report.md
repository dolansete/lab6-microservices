# Report
- The two services `accounts (2222)` and `web` are running and registered (two terminals, logs screenshots).
  To launch the registration service we use this command:
  ```
  ./gradlew :registration:bootRun
  ```
  To launch the accounts service we use this command:
  ```
  ./gradlew :accounts:bootRun
  ```
  ![accounts](https://github.com/dolansete/Imagenes/blob/main/Captura%20de%20pantalla%202022-01-02%20174828.png)
  
  To launch the webservice we use this command:
  ```
  ./gradlew :web:bootRun
  ```
  
  ![web](https://github.com/dolansete/Imagenes/blob/main/image.png)

- The service registration service has these two services registered (a third terminal, dashboard screenshots)
  To check if they are registered we will see the dashboard at ``` http://localhost:1111/ ```
  
  ![dashboard](https://github.com/dolansete/Imagenes/blob/main/Captura%20de%20pantalla%202022-01-02%20175845.png)
  
  As we can see, both services are registered with Eureka.

- A second `accounts` service instance is started and will use the port 4444. This second `accounts (4444)` is also
  registered (a fourth terminal, log screenshots).
  To do this, we have to change the line ```port:2222``` to ```port:4444``` at the file ```accounts\src\main\resources\application.yml``` and then use the command 
  ```./gradlew :accounts:bootRun``` 
  
  ![accounts2](https://github.com/dolansete/Imagenes/blob/main/Captura%20de%20pantalla%202022-01-02%20181435.png)
  
  
  After that, we check if it has been registered:
  
  ![dashboard2](https://github.com/dolansete/Imagenes/blob/main/Captura%20de%20pantalla%202022-01-02%20181228.png)
  
  As we can see,the new service has been registered succesfully.
- What happens when you kill the service `accounts (2222)` and do requests to `web`?  
  Can the web service provide information about the accounts again? Why?
  If we kill the service via Ctrl+C we can se at the dashboard that only the account service in the     port 4444 is UP. 
  The web service still works:
  
  ![web service](https://github.com/dolansete/Imagenes/blob/main/Captura%20de%20pantalla%202022-01-02%20184014.png)
  
  And it can provide information about the accounts:
  
  ![account info](https://github.com/dolansete/Imagenes/blob/main/Captura%20de%20pantalla%202022-01-02%20184209.png)
  
  This works because the web server asks for accounts by asking Eureka a logical name ACCOUNTS-SERVICE and Eureka translates it.
