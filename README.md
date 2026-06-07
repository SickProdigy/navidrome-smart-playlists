# Navidrome Smart Playlists

This folder is here to help people build and use Navidrome smart playlists.

The `.NSP` files in this folder are smart playlist definitions, not static song lists. Each file is a set of JSON rules that Navidrome can read during a library scan and turn into a playlist.

## What Smart Playlists Do

Smart playlists stay dynamic. Instead of manually adding songs one by one, you define rules like:

- songs from a genre
- songs from a year range
- loved or high-rated tracks
- tracks from or excluded by certain artists, albums, or tags

Navidrome applies those rules automatically, so the playlist updates as your library changes.

## How To Use

1. Save the `.NSP` file in a folder that Navidrome scans for playlists.
2. Run a library scan or quick scan in Navidrome.
3. Open the playlist in Navidrome and check that the results match what you wanted.

If the playlist does not appear, the file is usually in the wrong folder, the JSON is invalid, or the scan has not run yet.

## Basic File Structure

Most smart playlists here follow the same pattern:

- `title` is the playlist name shown in Navidrome.
- `comment` is a short description.
- `all` means every rule in the list must match.
- `any` means only one rule needs to match.
- `sort` and `order` control the result order.
- `limit` caps how many tracks the playlist returns.

Example ideas used in this folder:

- genre playlists such as Rock, Pop, Hip Hop, Metal, and Country
- decade playlists such as 70s, 80s, 90s, 2000s, and 2010s
- utility playlists such as Recently Added, Unrated, and Un-Played
- favorites and jukebox-style playlists for quick access

## Excluding Folders

Navidrome uses a `.ndignore` file to exclude folders or files from being added to the library.

- Put an empty `.ndignore` file in a folder to ignore that folder and everything under it.
- Or place one `.ndignore` file in your parent music folder and use `.gitignore`-style rules inside it.

Example:

```gitignore
# Ignore specific folders
/untagged/
/unsorted/

# Ignore a file type
*.flac

# Allow one specific album back in
!/favorite-album/*.flac
```

## Filename Order

The first character of the filename is used as a simple sorting trick for how playlists appear in Navidrome.

For example, a filename like `! Top Hip Hop ;).NSP` will appear near the top. While '_ Top Hip Hop ;).NSP' will appear near the bottom.

In this library, the leading characters are used in a rough order like this:

```text
!  #  $  &  '  (;  *  +  ,  -  .  ;  =  >  @  A-Z  ^  _
```

That makes it easier to group important playlists at the top and push utility playlists lower down.

This does not work well with different apps. For example, amperfy (iphone sub-sonic app) sorts '_ Top Hip Hop ;).NSP' as the top playlist, and 'Top Hip Hop ;).NSP' as the last playlist. 
So haven't quite figured out the best naming scheme that works well across all apps. For now, just be aware that the leading characters may affect playlist order differently in different apps.

## Further Reading

If you want to edit or create smart playlists, this Navidrome guide is a good reference:

- [How to Use Smart Playlists in Navidrome](https://gitea.sickgaming.net/sickprodigy/navidrome-smart-playlists/wiki/How-to-Use-Smart-Playlists-in-Navidrome)

It covers the JSON fields, operators, importing playlists, and a few examples you can adapt for your own Navidrome setup.