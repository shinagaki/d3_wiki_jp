[Part 1](https://github.com/mbostock/d3/wiki/Integrating-d3-with-a-CouchDB-database-1), 
[Part 3](https://github.com/mbostock/d3/wiki/Integrating-d3-with-a-CouchDB-database-3), 
[Part 4](https://github.com/mbostock/d3/wiki/Integrating-d3-with-a-CouchDB-database-4)

## Storing the D3 library in the CouchDB

This one is easy. First, make a copy of your complete **d3apps1** folder and store it in your workspace using the name **d3apps2**. Then just move a copy of **d3.v2.min.js** into the **_attachments** folder. Then it should look as follows:

```
d3apps2
    _attachments
        d3.v2.min.js
        index.html
        sp500.csv
    .couchapprc
```

Delete the references to the external d3 library files and insert a reference to the local **d3.v2.min.js** file. The beginning of your **index.html** file should look as follows (with or without the out-commented lines):

```
<!DOCTYPE html>
<meta charset="utf-8">
<!--
<script src="http://mbostock.github.com/d3/d3.js?2.7.2"></script>
<script src="http://mbostock.github.com/d3/d3.csv.js?2.7.2"></script>
<script src="http://mbostock.github.com/d3/d3.time.js?2.7.2"></script>
-->
<script src="d3.v2.min.js"></script>
```

From within your **d3apps2** folder, push your code into the CouchDB:

```
couchapp push d3apps2
```

Now D3 will be loaded from CouchDB.

## Storing the data in the CouchDB

First, under **_attachments** create a new file called **import.html**.
Then add the following code to **import.html**:

```
<html>

<head>
    <script src="/_utils/script/jquery.js"></script>
    <script src="/_utils/script/jquery.couch.js"></script>
    <script src="d3.v2.min.js"></script>
</head>

<body>

<script>

    // Adapt the values to your needs
    var file = "sp500.csv",
        dbName = "d3apps2",
        docId = "sp500",
        source = "FocusAndContext";

    d3.csv(file, function(data) {

        var doc = {
            _id : docId,
            souce : source,
            data : data
            // Add any fields you need
        };

        $.couch.db(dbName).saveDoc(doc, {
            success:function (data) {
                console.log("New doc created");
            },
            error:function (status) {
                console.log("error:", status);
            }
        });
    });

</script>

</body>
</html>
```

From within your **d3apps** folder, push your code into the CouchDB:

```
couchapp push d3apps2
```

Navigate to your import file:

```
http://127.0.0.1:5984/d3apps2/_design/d3apps2/import.html
```

That's it. The file is loaded and imports your data into CouchDB. You may control your import by navigating to 

```
http://127.0.0.1:5984/_utils/database.html?d3apps2
```

There you find a new document named **"sp500"**. If you click on it, you can drill down to individual data.

**A Warning:** This import file is just a quick hack to get data into the CouchDB. There's no error checking. You can execute this import only once. If something goes wrong, you have to delete "sp500" manually using Futon, the rudimentary database manager of CouchDB, fix the error and try again. After the data has been imported successfully, it's no longer needed in this application. But don't yet delete it. You need it for the third part. And keep the **import.html** file, because you might want to import additional datasets into your CouchDB database, using the same import pattern.

How you can access the data in CouchDB from your D3 application, is shown in [Integrating D3 with a CouchDB database 3](https://github.com/mbostock/d3/wiki/Integrating-D3-with-a-CouchDB-database-3).