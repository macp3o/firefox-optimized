# Firefox Optimized

*Optimizing the Firefox browser.*

## Introduction

These tweaks optimize video and responsiveness of the most recent version of Firefox browser.

The fixes are particularly beneficial for older and slower systems with limited memory.

## Settings

Enter `about:config` in the address bar of Firefox, and agree to the warning  that appears.

In the filter box below the address bar, type the filter keyword from the table below. Then, select the corresponding setting in the list, and change it's value to the  value shown in the table by double clicking on it, after reading the notes below the table. Repeat for each row.

|      | Filter          | Setting                                                | Value |                                                       |
| --- | -------------- | :---------------------------------------------: | :-------: | ----------------------------------------| 
| 1   | ipv6           | network.dns.disableIPv6              | true    | no IPv6 from my ISP              |
| 2   | predictor | network.predictor.enabled          | false   | no preloading linked pages |
| 3   | prefetch   | network.prefetch-next                  | false   | |
| 4   | prefetch   | network.dns.disablePrefetch      | true    | |
| 5   | pipelining | network.http.pipelining               | true   | multiple requests per connection |
| 6   | workers    | dom.workers.maxPerDomain        | 4   | few web workers                      |
| 7   | workers    | dom.workers.sharedWorkers.enabled | false | |
| 8   | zoom         | browser.zoom.updateBackgroundTabs | false | less UI freezes on zoom|
| 9   | gmp            | media.gmp-provider.enabled | false | faster video playback|
| 10 | autostart | browser.tabs.remote.autostart| false | makes FF49 usable|
| 11 | autostart | browser.tabs.remote.autostart.2 | false | makes FF49 usable |

#### No IPv6
The first setting disables IPv6 lookups. Apply only if IPv6 is not available in your network (which is frequently the case). It does not make Firefox noticeably faster, but reduces lag and makes me feel better :)

#### No Speculative Preloading
Settings 2-4 turn off speculative preloading of domain names and pages that are linked from the current page. This is expected to make navigating to a subsequent link instantaneous. This is great, but it bringsdownsides: It bogs down bandwidth unnecessarily, can preload undesired (and sometimes undesirable) content, and generates misleading server hits (e.g. negatively affecting content recommenders).

#### Pipelining Enabled
Setting 5 allows several requests to be sent to the server over a single connection. This is faster than establishing separate connections for each request.

#### Limited Web Workers
Settings 6-7 limit web workers. Web workers were freezing the desktop UI by accessing the disk aggressively everytime I opened additional tabs. I initially faulted the disk cache, but after troubleshooting, I found that web workers were running disk intensive tasks. I started by disabling web workers, making Firefox became usable again. Howver, web workers are required in Firefox 49 to prevent crashes (Firefox 49.0 crashes with dom.workers,maxPerDomain set to 1). You may need web workers for some unusual applications.

#### UI Zoom
Setting 8 minimizes freezes to the UI after zooming in or out.

#### No H.264 Video
Setting 9 forces Firefox to not use H.264 video, since it's not yet hardware optimized on Linux and Windows.

#### No Multi-process Firefox
Settings 10 and 11 toggle FF multi-process off. Multi-process blocks the display of all tabs and windows for several minutes (sometimes 10, 15, 20 minutes) when using the default settings and more than a few tabs or windows open. Disabling multi-process makes it fast again.


## License

Licensed under the [MIT License](LICENSE.md). 



