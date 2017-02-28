
SETUP basic query:
```
https://services1.arcgis.com/g2TonOxuRkIqSOFx/arcgis/rest/services/st_louis_bat_sightings/FeatureServer/0/query?f=json&where=1=1&outFields=*
```

ADD tests automation:
```
var jsonData = JSON.parse(responseBody);
postman.setEnvironmentVariable("objectId", jsonData.addResults[0].objectId);
```


Code:

```
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "https://services1.arcgis.com/g2TonOxuRkIqSOFx/arcgis/rest/services/st_louis_bat_sightings/FeatureServer/0/applyEdits",
  "method": "POST",
  "headers": {
    "origin": "https://ps-dbs.maps.arcgis.com",
    "user-agent": "Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/56.0.2924.87 Safari/537.36",
    "content-type": "application/x-www-form-urlencoded",
    "accept": "*/*",
    "dnt": "1",
    "referer": "https://ps-dbs.maps.arcgis.com/home/webmap/viewer.html?webmap=fcfb7fc90ab14e5086c8f10d9adf9931",
    "accept-encoding": "gzip, deflate, br",
    "accept-language": "en-US,en;q=0.8",
  },
  "data": {
    adds: `[{"geometry":{"x":-10050926.056063754,"y":4669496.21517963,"spatialReference":{"wkid":102100,"latestWkid":3857}},"attributes":{"lon":null,"lat":null}}]`,
    f: `json`
  }
};

$.ajax(settings).done(function (response) {
  console.log(response);
});
```


Tests:

```
tests['Added succesfully'] = responseBody.has('"success":true')
```
