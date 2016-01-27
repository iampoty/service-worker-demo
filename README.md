#API Tracker [Kapook]

#####tracking#####

#####URL##### http://202.183.165.1:2223/

#####Method##### POST

#####JSON Data#####
```
fbid	string
age   int
gender int   [1:male, 2:female,...]
device	string ["ios","android",...]
portal	int
category	int
contented	int
locationname  string
location GeoPoint /map(string:float)/  {"lat":7.950868,"lon":98.336633}
datetime int [timestamp in unix]
```


#####Example#####
```
{
"transid":"1234",
"data":[{
  "fbid":"fb12344",
  "age":20,
  "gender":1,
  "device":"ios",
  "portal":27,
  "category":9,
  "contentid":12227,
  "locationname":"phuket",
  "location":{
    "lat":7.950868,
    "lon":98.338633
  },
  "datetime":1453803322
  }]
}
```

Response:
status string ["ok","error"]
detail string

{
status:"ok",
detail:""
}


PHP Example:

```
<?php
    $data = json_encode(array(      
        'transid' => $transid,
        'data' => array(array(
                'fbid' => "1234",
                'device' => "ios",
                'tags' => "movie,ost,batman",
                'gender' => 1,
                'age' => 24,
                'portal' => 27,
                'contentid' => 10227,
                'category' => 9,
                'locationname' => 'bangkok',
                'location' => array('lat' => 7.950868,'lon' => 98.338633),
                'datetime' => time(),
            ),),
    ));
    $results = file_get_contents('http://202.183.165.1:2223/', false, stream_context_create(array('http' => array('method' => 'POST', 'content' => $data))));
    echo "<br>$i : $transid :\$results " . htmlspecialchars($results);
?>
```
