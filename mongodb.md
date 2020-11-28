## Helpful MongoDB Snippets
Here is the documentation: *http://mongodb.github.io/node-mongodb-native/3.4/quick-start/quick-start/*


### Test if you are connected
``` 
client.connect(function(err) {
  assert.equal(null, err);
  console.log("Connected successfully to server");

  const db = client.db(dbName);

  client.close();
});
```




### Find all the entrys 
```
const findDocuments = function(db, callback) {
  // Get the documents collection
  const collection = db.collection('documents');
  // Find some documents
  collection.find({}).toArray(function(err, docs) {
    assert.equal(err, null);
    console.log("Found the following records");
    console.log(docs)
    callback(docs);
  });
}
```



### Insert an entry
```
const insertDocuments = function(db, callback) {
  // Get the documents collection
  const collection = db.collection('documents');
  // Insert some documents
  collection.insertMany([
    {a : 1}, {a : 2}, {a : 3}
  ], function(err, result) {
    assert.equal(err, null);
    assert.equal(3, result.result.n);
    assert.equal(3, result.ops.length);
    console.log("Inserted 3 documents into the collection");
    callback(result);
  });
}
```

### Important Note 
Establish a connection once and then put all the middlewarestuff inside this connection.

```
client.connect(function(err) {
  // parse incoming data as json IMPORTANT!
  app.use(express.json({limit: '1mb'}));
  app.use(express.static('public'));
  
  app.listen(port, () => {
      console.log(`Example app listening at http://localhost:${port}`)
    })

  const db = client.db(dbName);
  const activitesCollection = db.collection('activities')

  app.post('/example', (req, res) => {
      // insert for example
    });

    app.get('/example', (req, res) => {
      // get the entrys for example
      })
    .catch(error => console.error(error))
 });
 });
```

