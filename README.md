![]<img src="logo.png" width="256" height="348">


InstaFarmer is a modern Javascript library (API) for Instagram automation/bot that utilizes Google's Puppeteer. Its aim is to provide a straightforward setup, user-friendly experience, and flexibility to abide by Instagram's regulations.



## Setup

- First install [Node.js](https://nodejs.org/en/) 8 or newer.
  - On MacOS, it's recommended to use [homebrew](https://brew.sh/): `brew install node`

- Create a new directory with a file like [instaFarmer.js](https://github.com/smoo7h/instaFarmer/blob/master/instaFarmer.js)

- Adjust your `instaFarmer.js` to your needs. If you want to see how it would work without doing any invasive actions, use the `dryRun: true` option. Toggle `headless` to see it in action.

- Modify settings in appsettings.js

- Add user and password to .env

- Open a terminal in the directory

- Run `npm i -g yarn`

- Run `yarn add puppeteer instauto`

- Run `node example`

You can run this code for example once every day using cron or pm2 or similar

## Supported functionality

- Follow the followers of some particular users. (e.g. celebrities.) Parameters like max/min ratio for followers/following can be set.

- Unfollow users that don't follow us back. Will not unfollow any users that we recently followed.

- Unfollow auto followed users (also those following us back) after a certain number of days.

- The code automatically prevents breaching 100 follow/unfollows per hour or 700 per 24hr, to prevent bans. This can be configured.


## Tips
- Run this on a machine with a non-cloud IP to avoid being banned

## Troubleshooting

- If it doesn't work, make sure your instagram language is set to english

## Running on Raspberry Pi

Because puppeteer chrome binaries are not provided for RPi, you need to first install chromium using apt.

Then replace your puppeteer launch code:

```js
browser = await puppeteer.launch({
    executablePath: '/usr/bin/chromium-browser',
    headless: true,
    args: ['--disable-features=VizDisplayCompositor'],
});
```

See also:
- https://github.com/GoogleChrome/puppeteer/issues/550
- https://github.com/GoogleChrome/puppeteer/issues/3774

Also you might want to install the more lightweight package `puppeteer-core` instead of `puppeteer`.

## Running with pm2
First install [pm2](https://github.com/Unitech/pm2). (`npm i -g pm2`) Then copy [instabot.yml](https://github.com/smoo7h/InstaFarmer/blob/master/instabot.yml) into the same dir as `instaFarmer.js` and run:

```bash
pm2 start instabot.yml
pm2 save
pm2 startup
```

Now it will run automatically on reboot

## Support Me 

This project is maintained by me alone. The project will always remain free and open source, but if it's useful for you, consider supporting me by following me on twitter

Follow me on [Twitter](https://twitter.com/Matty_McCann)
