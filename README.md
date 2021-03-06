# Sonarr Torrent Cleaner

Simple executable to remove torrents and optionally blacklist them if they haven't progressed in a set time period

## Usage

- Copy the provided `config.default.json` to `config.json` and set it up to your preference
- Run the executable every x minutes using an external program such as cron (Built in scheduling coming soon) (Recommended time 15 minutes)

## Config

``` json
{
    //Time to wait on a torrent that has made no progress before removing it (Time format: https://golang.org/pkg/time/#ParseDuration)
    "WaitTime": "4h",
    // Your Sonarr api key
    "SonarrAPIKey": "xxxxxxxxxxxxxxxx",
    // The address your Sonnarr install can be found at
    "SonarrURL": "http://localhost",
    // The amount of time to wait for a torrent to get past 0% before removing it
    "ZeroPercentTimeout": "1h",
    // Blacklist the torrent in Sonarr so it's not downloaded again (Time format: https://golang.org/pkg/time/#ParseDuration)
    "Blacklist" : true
}
```

## Scheduling

Currently this does not have a built in scheduler, on linux this is easy to do with cron (see below) on windows you have a few options [see here](https://stackoverflow.com/a/132975)

`*/10 *  * * *   my_username  cd /home/my_username/TorrentCleaner/ && /home/my_username/TorrentCleaner/SonarrTorrentCleaner_lin`
Will run TorrentCleaner every 10 minutes
