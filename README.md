# stakk-content

This repository tracks content for [stakk](https://stakk.ltd).

## Adding a stack

stacks are added as JSON files. You can validate your JSON files [here](https://jsonlint.com/). If you are unsure, check out one of the existing stacks.

1. add a folder with your desired username to `/data`.
2. in `/data/${username}`, add a file `${stackname}.json`. If your stack should be named mixtapes, name the file `mixtapes.json`. You can have more than one stack if you like.
3. fill in stack content

```json
{
  "title": "mixtapes",
  "slug": "dev",
  "author": {
    "name": "Felix",
    "slug": "felix",
    "url": "https://spoettel.dev"
  },
  "theme": {
    "background": "#FFD600",
    "text": "#34332B"
  },
  "items": []
}
```

* `title` - the name of your stack. this can be capitalized.
* `slug` - the slug of this mix. **only lowercase letters and `-`, no spaces**
* `author`
  * `name` - your name. this can be capitalized.
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
      "createdAt": "2020-12-01T00:00:00Z",
      "id": "ckqz4ftbt000101mpft7df8rc",
      "slug": "velveteen",
      "title": "Velveteen",
      "genres": [
        "Glam Rock",
        "Britpop"
      ],
      "mixcloudId": "/mcmirage/velveteen/",
      "spotifyId": "1Kiw8zXc8A0Mpt2TdqH7DZ",
      "tracklist": [
        {
          "artist": "Alice Cooper",
          "title": "Hello Hooray!",
          "at": "00:00"
        }
      ]
    },
```

* `createdAt` the date this mix was created as an ISO timestamp. get one [here](https://timestampgenerator.com/)
* `id` a unique id. get one [here](https://www.getuniqueid.com/cuid)
* `title` the title of this item. can be capitalized
* `slug` the slug of your user. **only lowercase letters and `-`, no spaces**
* `genres` up to **two** genres / tags
* `mixcloudId` (optional) if this is a mixcloud mix, add the id here.
* `spotifyId` (optional) if this item has a spotify playlist, add the id here
* `tracklist` an array of tracks. each track looks liks this:
  * `artist`
  * `title`
  * `at` (optional) only set if this is a continuous mix

## Adding a cover

You can add a cover to your mix by placing an image into `./assets`. The file name **needs to match the slug of the item**. If your item is called `awesome-mix`, the filename needs to be `awesome-mix.jpg`.

The file should be **square**. The minimum size is 600x600, preferably 1200x1200. Larger images are automatically optimized but please keep it reasonable as this affects build times. Ideally, you add **1200x1200** images here.

## Your Urls

Once you added a stack, it will be available on: `https://stakk.ltd/{user.slug}/{stack.slug}`  
Individual items in the stack are available via: `https://stakk.ltd/{user.slug}/{stack.slug}/{item.slug}` (In this case, your stack will be displayed with the wanted item at the top)  
There is a RSS feed for your stack at: `https://stakk.ltd/rss/{user.slug}/{stack.slug}`  
