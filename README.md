Starting steps
1. Use the following command to start the payment-server project.
   
       java -jar -DserverPort=8090 payment-server-1.0.jar
   note: You can specify the starting port through the parameter "-DserverPort="

  
2. Use the following command to start the payment-client project.
 
        java -jar -DserverPort=8090 -DfilePath=D:\\Payment.txt payment-client-1.0.jar
   note:
   - You can specify the service port to connect through the parameter "-DserverPort="
    
   -  Once you specify the "-DfilePath=" parameter, the program will automatically load the contents of the file and automatically send the payment records in the format to the remote end
    
   -  This "-DfilePath=" parameter currently only supports the absolute path of the window system.
   - In addition, you can also start the program without specifying a file, the program will not load the file, and you can use the command mode to interact

EndPoints

1.Request/Response - use currency Code as input then payment number as output.
               
      GET http://{serverIp}:{serverPort}/query/payment/currency/{currencyCode}
- for example
          
      GET http://localhost:8090/query/payment/currency/USD

2.Server Sent Event - use currency code as input then stream out the payment (when payment is updated).

      GET http://{serverIp}:{serverPort}/subscribe/payment/currency/{currencyCode}
- for example

      GET http://localhost:8089/subscribe/payment/currency/USD
