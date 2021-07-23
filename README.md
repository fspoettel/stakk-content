# stakk-content

This repository tracks content for [stakk](https://stakk.ltd). You are welcome to add your own stack to it by following the instructions below.

## Adding a stack

stacks are added as JSON files. You can validate your JSON files [here](https://jsonlint.com/). If you are unsure, check out one of the existing stacks.

1. add a folder with your desired username to `/data`.
2. in `/data/${username}`, add a file `${stackname}.json`. If your stack is named _mixtapes_, name the file `mixtapes.json`. You can have more than one stack if you like.
3. add content to the file:

```json
{
  "title": "Nice Mixtapes",
  "slug": "nice-mixtapes",
  "author": {
    "name": "Felix S",
    "slug": "felix-s",
    "url": "https://some-url.com"
  },
  "theme": {
    "background": "#FFD600",
    "text": "#34332B"
  },
  "items": []
}
```

* `id` a unique id. get one [here](https://www.getuniqueid.com/cuid)
* `title` - the title of this stack
* `slug` - the slug of this mix. **only lowercase letters and `-`, no spaces**
* `author`
  * `name` - your name
  * `slug` - the slug of your user. **only lowercase letters and `-`, no spaces**
  * `url` - a link for your user name
* `theme` (optional)
  * `background` (optional) a hex code. leave empty or set to `null` (without quotes) for the default theme.
  * `text` (optional) a hex code. leave empty or set to `null` (without quotes) for the default theme.
* `items` see below

## Adding a stack item

Items are added to the `items` array in your mix. New items are added to the bottom of the array. Each item should look like this:

```json
    {
      "createdAt": "2021-07-01T00:00:00Z",
      "id": "ckqz4g09c000301mpeti04vdg",
      "title": "Come to my Garden",
      "slug": "come-to-my-garden",
      "links": [
        "https://www.mixcloud.com/mcmirage/come-to-my-garden/",
        "https://open.spotify.com/playlist/3877PFqx7sGMccAWA7tInU",
        { "title": "Stream", "url": "https://instagram.com" }
      ],
      "tags": [
        "Baroque Pop",
        "Psych. Pop"
      ],
      "tracklist": [
        {
          "artist": "Minnie Riperton",
          "title": "Come To My Garden",
          "at": "00:00"
        },
        {
          "artist": "Hildgard Knef",
          "title": "Insel meiner Angst",
          "at": "03:15"
        }
      ]
    }
```

* `createdAt` the date this mix was created as an ISO timestamp. get one [here](https://timestampgenerator.com/)
* `id` a unique id. get one [here](https://www.getuniqueid.com/cuid)
* `title` the title of this item
* `slug` the slug of your user. **only lowercase letters and `-`, no spaces**
* `tags` (optional) up to **two** tags
* `links` (optional). an array of links. a link can either be:
  * a `url` - use this for spotify playlists or mixcloud mixes. we handle these automatically.
  * an `object` - use this for custom links. You need to enter a `title` and `url` in this case.
* `tracklist` an array of tracks. each track looks liks this:
  * `artist`
  * `title`
  * `at` (optional) only set if this is a continuous mix, leave blank for spotify.

## Adding a cover to an item

You can add a cover to your mix by placing an image into `./assets`. The file name **needs to match the slug of the item**. If your item is called `awesome-mix`, the filename needs to be `awesome-mix.jpg`.

The file should be **square**. The minimum size is 600x600, preferably 1200x1200. Larger images are automatically optimized but please keep it reasonable as this affects build times. Ideally, you add **1200x1200** images here.

## Submitting your entry

Submit a PR with your stack. Once merged, a build will start and your stack will be published.

## URLs

Once you added a stack, it will be available on: `https://stakk.ltd/{user.slug}/{stack.slug}`

Your latest stack will also be available at: `https://stakk.ltd/{user.slug}`

Individual items in the stack are available via: `https://stakk.ltd/{user.slug}/{stack.slug}/{item.slug}`. In this case, the referenced item will be on top of the stack.

There is a RSS feed for your stack at: `https://stakk.ltd/rss/{user.slug}/{stack.slug}.xml`

## Why a Github repo?

This started as a static website I built for myself. I'm currently trying to figure out whether to turn this into an app and this is a stopgap solution. If you have a use case for this that is not music, please [get in touch](https://stakk.ltd/about).
