# romania.json
romania.json is just a bunch of `.json` files that contain data about states, cities and even institutions from Romania. It provides a consistent way of storing it, since there's a lot to search on the internet to find these.

# What's in the box?
* Regions with its own cities. Each city has a corresponding ZIP Code and the map coordinates.
* **[BETA]** Regions with its institutions (schools & high-schools)

# Where's the download button?
The latest (minifed; production-ready) `.json` files are available on the [Releases page](https://github.com/rennokki/romania.json/releases) for download.

# Implementation examples
Since the JSON files are big (even minified), the only way to use it for high-traffic applications is to cache it and invalidate it when needed. Here's an example on how to use it in PHP:
```php
$regions = json_decode(file_get_contents('json/regions.json'));

foreach ($regions as $regionName => $cities) {
  // $regionName is the name of the region
  // $cities contains all the cities

  foreach ($cities as $city) {
    // $city->name
    // $city->zip
    // $city->lat
    // $city->long
  }
}
```

It's even more useful when using it in forms. Here's an example using blade syntax:

```
<select name="region">
  @foreach ($regions as $regionName => $cities)
    <option value="{{ $regionName }}">{{ $regionName }}</option>
  @endforeach
</select>
```

# I spot a mistake!
If you spot a mistake or simply want to contribute, a PR with the changes is enough. The only thing to stick with is the consistency.
