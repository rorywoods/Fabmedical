# Fabmedical Exercise 2 Alternative
These instructions use the content-init script to load the Cosmos DB database instead of migrating.


1. In the Azure Portal, navigate to your Cosmos DB resource
![image](https://user-images.githubusercontent.com/987114/145730399-4a724041-9fcb-4975-b13f-374629cedfc1.png)
1. Open the `Quick Start` blade and the Node.js tab  
1. Copy the Primary Connection String to your clipboard  
![image](https://user-images.githubusercontent.com/987114/145732330-737b4c20-6872-4774-b75a-040a62bf939b.png)
1. Modify the copied connection string by adding the database `contentdb` to the URL, and three querystring parameters `ssl=true&replicaSet=globaldb&retrywrites=false`. The resulting connection string should look like the below sample. Note that you may need to modify the endpoint URL.
   ```
   mongodb://<USERNAME>:<PASSWORD>@fabmedical-<SUFFIX>.mongo.cosmos.azure.com:10255/contentdb?ssl=true&replicaSet=globaldb&retrywrites=false
   ```
3. Create a `MONGODB_CONNECTION` environment variable with this value on your Build VM. Surround the connection string with quotes.
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
