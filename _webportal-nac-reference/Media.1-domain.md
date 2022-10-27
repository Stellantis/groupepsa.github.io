---
layout: api-reference
section: webportal
subsection: v1
categorie: API Reference
title: References
name: Media
supported:
  - 2
  - 3
  - 4
type: class
---

#### OVERVIEW

Provides the methods to interact with the Media player.

#### METHODS SUMMARY

Method | Response Type | Description
-----|----|----
[Media.GetAlbumName()]({{ site.baseurl }}/webportal/v1/reference/list/#api-Media-GetAlbumName) |  String | Gets the album name.
[Media.GetArtistName()]({{ site.baseurl }}/webportal/v1/reference/list/#api-Media-GetArtistName) | String | Gets the artist name.
[Media.GetCurrentTrack()]({{ site.baseurl }}/webportal/v1/reference/list/#api-Media-GetCurrentTrack) | Number | Gets the current track number.
[Media.GetFolderName()]({{ site.baseurl }}/webportal/v1/reference/list/#api-Media-GetFolderName) | String | Returns the folder where the current media is located.
[Media.GetMediaState()]({{ site.baseurl }}/webportal/v1/reference/list/#api-Media-GetMediaState) | Number | Gets the current state of the media.
[Media.GetTotalTracks()]({{ site.baseurl }}/webportal/v1/reference/list/#api-Media-GetTotalTracks) | Number | Gets the total number of tracks.
[Media.GetTrackName()]({{ site.baseurl }}/webportal/v1/reference/list/#api-Media-GetTrackName) | String | Gets the name of the current track.
[Media.GetTypeName()]({{ site.baseurl }}/webportal/v1/reference/list/#api-Media-GetTypeName) | Number | Returns the current media's type.
[Media.audio.configure()]({{ site.baseurl }}/webportal/v1/reference/list/#api-Media-Audio-configure) | None | Connects or disconnects an audio source.

#### EVENTS SUMMARY

Event | Description
----|----
[Media.Audio.audioAvailable]({{ site.baseurl }}/webportal/v1/reference/list/#event-Media-Audio-audioavailable) | Triggered when audio source is connected.
[Media.Audio.audioLost]({{ site.baseurl }}/webportal/v1/reference/list/#event-Media-Audio-audioLost) | Triggered when audio source is disconnected.
