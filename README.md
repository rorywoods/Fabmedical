# Fabmedical Exercise 2 Alternative
These instructions use the content-init script to load the Cosmos DB database instead of migrating.


1. In the Azure Portal, navigate to your Cosmos DB resource
![image](https://user-images.githubusercontent.com/987114/145730399-4a724041-9fcb-4975-b13f-374629cedfc1.png)
1. Select `Connection String` under `Settings`  
1. Copy the Primary Connection String to your clipboard  
![image](https://user-images.githubusercontent.com/987114/145730459-69bc5244-6357-43ac-a4ee-492cbb77bf4c.png)
1. Create a `MONGODB_CONNECTION` environment variable with this value on your Build VM. Surround the connection string with quotes.
   ```bash
   export MONGODB_CONNECTION="<connection_string>"
   ```
1. Run the init script
   ```bash
   cd ~/Fabmedical/content-init
   nodejs server.js
   ```
1. Use the Cosmos DB Data Explorer to verify the collections and documents were created
   ![image](https://user-images.githubusercontent.com/987114/145730681-c887bd6d-0219-4d26-a126-496c857eaf37.png)
