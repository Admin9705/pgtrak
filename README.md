# PGTrak
Script to add new shows & movies to Sonarr/Radarr based on Trakt lists.

* Original Script Author - https://github.com/l3uddz/traktarr
* Read Changes - https://github.com/l3uddz/traktarr/compare/master...Admin9705:master

# Configuration

```
{
  "core": {
    "debug": false
  },
  "filters": {
    "movies": {
      "allowed_countries": [
        "us",
        "gb",
        "ca"
      ],
      "blacklist_title_keywords": [
        "untitled",
        "barbie"
      ],
      "blacklisted_genres": [
        "documentary",
        "music"
      ],
      "blacklisted_min_runtime": 60,
      "blacklisted_min_year": 2000
    },
    "shows": {
      "allowed_countries": [
        "us",
        "gb",
        "ca"
      ],
      "blacklisted_genres": [
        "animation",
        "game-show",
        "talk-show",
        "home-and-garden",
        "children",
        "reality",
        "anime",
        "news",
        "documentary",
        "special-interest"
      ],
      "blacklisted_min_runtime": 15,
      "blacklisted_min_year": 2000,
      "blacklisted_networks": [
        "twitch",
        "youtube",
        "nickelodeon",
        "hallmark",
        "reelzchannel",
        "disney",
        "cnn",
        "cbbc",
        "the movie network",
        "teletoon",
        "cartoon network",
        "espn",
        "yahoo!",
        "fox sports"
      ]
    }
  },
  "radarr": {
    "api_key": "",
    "profile": "HD-1080p",
    "root_folder": "/movies/",
    "url": "http://localhost:7878"
  },
  "sonarr": {
    "api_key": "",
    "profile": "HD-1080p",
    "root_folder": "/tv/",
    "url": "http://localhost:8989"
  },
  "trakt": {
    "api_key": ""
  }
}
```


# Usage

## Help

```
Usage: python3 traktarr.py movies --help
Usage: python3 traktarr.py shows --help
```


## Movies

```
Usage: python3 traktarr.py movies [OPTIONS]

  Add new movies to Radarr.

Options:
  -t, --list-type [anticipated|trending|popular]
                                  Trakt list to process.  [required]
  -l, --add-limit INTEGER         Limit number of movies added to Radarr.
                                  [default: 0]
  -d, --add-delay FLOAT           Seconds between each add request to Radarr.
                                  [default: 2.5]
  --no-search                     Disable search when adding movies to Radarr.
  --help                          Show this message and exit.
```


## Shows

```
Usage: python3 traktarr.py shows [OPTIONS]

  Add new shows to Sonarr.

Options:
  -t, --list-type [anticipated|trending|popular]
                                  Trakt list to process.  [required]
  -l, --add-limit INTEGER         Limit number of shows added to Sonarr.
                                  [default: 0]
  -d, --add-delay FLOAT           Seconds between each add request to Sonarr.
                                  [default: 2.5]
  --no-search                     Disable search when adding shows to Sonarr.
  --help                          Show this message and exit.
```

## Example

```
python3 traktarr.py movies -t anticipated -l 10

```

```
python3 traktarr.py shows -t popular -l 2
```
