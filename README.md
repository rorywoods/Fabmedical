# Fabmedical Exercise 1 Alternative
These instructions use the content-init script to load the Cosmos DB database instead of migrating.


1. In the Azure Portal, navigate to your Cosmos DB resource
![image](https://user-images.githubusercontent.com/987114/145730399-4a724041-9fcb-4975-b13f-374629cedfc1.png)
1. Open the `Quick Start` blade and the Node.js tab  
1. Copy the Nodejs 3.0 Primary Connection String to your clipboard  
![image](https://user-images.githubusercontent.com/987114/146229610-e147a973-576a-4c50-bf77-0eaf6ee0fe0f.png)
1. Modify the copied connection string by adding the database `contentdb` to the URL (after the `10255/`), and the querystring parameter `replicaSet=globaldb`. The resulting connection string should look like the below sample. 
   ```
   mongodb://<USERNAME>:<PASSWORD>@fabmedical-<SUFFIX>.mongo.cosmos.azure.com:10255/contentdb?replicaSet=globaldb&ssl=true&retrywrites=false...
   ```
3. On the Build Agent VM in your Cloud Shell session, create a `MONGODB_CONNECTION` environment variable with this value. Surround the connection string with quotes.
   ```bash
   export MONGODB_CONNECTION="<connection_string>"
   ```
1. Run the init script to populate Cosmos DB
   ```bash
   cd ~/Fabmedical/content-init
   npm install
   nodejs server.js
   ```
1. Use the Cosmos DB Data Explorer to verify the collections and documents were created
   ![image](https://user-images.githubusercontent.com/987114/146230086-7c1d2ba3-2eac-4607-976a-61b5bc2b9444.png)
