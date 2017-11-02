# jq-tutorial
Sample Examples for Jq article - OSFY December '17 Edition


## Examples

##### Fetch raw json using curl 

```bash 
curl -sS https://www.metaweather.com/api/location/search/?query=new 
```

Output:

```bash
[{"title":"New York","location_type":"City","woeid":2459115,"latt_long":"40.71455,-74.007118"},{"title":"New Delhi","location_type":"City","woeid":28743736,"latt_long":"28.643999,77.091003"},{"title":"New Orleans","location_type":"City","woeid":2458833,"latt_long":"29.953690,-90.077713"},{"title":"Newcastle","location_type":"City","woeid":30079,"latt_long":"54.977940,-1.611620"},{"title":"Newark","location_type":"City","woeid":2459269,"latt_long":"40.731972,-74.174179"}]
```

##### Prettify using Jq

```bash
curl -sS https://www.metaweather.com/api/location/search/?query=new 
```

Output:

```bash
[
  {
    "title": "New York",
    "location_type": "City",
    "woeid": 2459115,
    "latt_long": "40.71455,-74.007118"
  },
  {
    "title": "New Delhi",
    "location_type": "City",
    "woeid": 28743736,
    "latt_long": "28.643999,77.091003"
  },
  {
    "title": "New Orleans",
    "location_type": "City",
    "woeid": 2458833,
    "latt_long": "29.953690,-90.077713"
  },
  {
    "title": "Newcastle",
    "location_type": "City",
    "woeid": 30079,
    "latt_long": "54.977940,-1.611620"
  },
  {
    "title": "Newark",
    "location_type": "City",
    "woeid": 2459269,
    "latt_long": "40.731972,-74.174179"
  }
]

```
<img src="images/comparsion.png" height="600">

##### Display first element of array

```bash 
curl -sS https://www.metaweather.com/api/location/search/?query=new | jq '.[0]'
```

Output: 

```bash
{
  "title": "New York",
  "location_type": "City",
  "woeid": 2459115,
  "latt_long": "40.71455,-74.007118"
}
```

##### Display City Names for all

```bash
curl -sS https://www.metaweather.com/api/location/search/?query=new | jq '.[] | .title'
```

Output:

```bash
"New York"
"New Delhi"
"New Orleans"
"Newcastle"
"Newark"
```

##### Display City Names along with ID for all 
```bash
curl -sS https://www.metaweather.com/api/location/search/\?query\=new | jq '.[] | .title,.woeid'
```

Output:

```bash
"New York"
2459115
"New Delhi"
28743736
"New Orleans"
2458833
"Newcastle"
30079
"Newark"
2459269
```

##### String Interpolation

```bash
curl -sS https://www.metaweather.com/api/location/search/\?query\=new | jq '.[] |  "For \(.title) code is \(.woeid)"'
```

Output:

```bash
"For New York code is 2459115"
"For New Delhi code is 28743736"
"For New Orleans code is 2458833"
"For Newcastle code is 30079"
"For Newark code is 2459269"
```

<img src="images/basic_filters.png">