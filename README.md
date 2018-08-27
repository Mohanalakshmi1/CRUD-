# CRUD-
var MongoClient = require('mongodb').MongoClient
 , assert = require('assert');

var url = 'mongodb://localhost:27017/myproject';
MongoClient.connect(url, function(err, db) {
  assert.equal(null, err);
  console.log("Connected correctly to server");
  db.collection('inserts').insertOne({a:1}, function(err, r) {
    assert.equal(null, err);
    assert.equal(1, r.insertedCount);
    db.collection('inserts').insertMany([{a:2},{a:3}], function(err, r) {
      assert.equal(null, err);
      assert.equal(2, r.insertedCount);
 db.close();
    });
  });
var MongoClient = require('mongodb').MongoClient
 , assert = require('assert');
var url = 'mongodb://localhost:27017/myproject';
MongoClient.connect(url, function(err, db) {
  assert.equal(null, err);
  console.log("Connected correctly to server");

  var col = db.collection('updates');
  col.insertMany([{a:1}, {a:2}, {a:2}], function(err, r) {
    assert.equal(null, err);
    assert.equal(3, r.insertedCount);
    col.updateOne({a:1}, {$set: {b: 1}}, function(err, r) {
      assert.equal(null, err);
      assert.equal(1, r.matchedCount);
      assert.equal(1, r.modifiedCount);
      col.updateMany({a:2}, {$set: {b: 1}}, function(err, r) {
        assert.equal(null, err);
        assert.equal(2, r.matchedCount);
        assert.equal(2, r.modifiedCount);
        col.updateOne({a:3}, {$set: {b: 1}}, {
          upsert: true
        }, function(err, r) {
          assert.equal(null, err);
          assert.equal(0, r.matchedCount);
          assert.equal(1, r.upsertedCount);
          db.close();
        });
      });
    });
  });
var MongoClient = require('mongodb').MongoClient
 , assert = require('assert');
var url = 'mongodb://localhost:27017/myproject';
MongoClient.connect(url, function(err, db) {
  assert.equal(null, err);
  console.log("Connected correctly to server");

  var col = db.collection('removes');
  col.insertMany([{a:1}, {a:2}, {a:2}], function(err, r) {
    assert.equal(null, err);
    assert.equal(3, r.insertedCount);
    col.deleteOne({a:1}, function(err, r) {
      assert.equal(null, err);
      assert.equal(1, r.deletedCount);
      col.deleteMany({a:2}, function(err, r) {
        assert.equal(null, err);
        assert.equal(2, r.deletedCount);
        db.close();
      });
    });
  });
});
});
});
# Function to delete record from mongo db
def delete():
    try:
    criteria = raw_input('\nEnter employee id to delete\n')
        db.Employees.delete_many({"id":criteria})
    print '\nDeletion successful\n' 
    except Exception, e:
    print str(e)
