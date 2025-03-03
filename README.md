# Axilla

A web-based implementation of [Pixlet](https://github.com/tidbyt/pixlet) which is used to develop [Tidbyt](https://tidbyt.com/) applications.

See it live: [`axilla.netlify.app`](https://axilla.netlify.app)

![AXILLA](https://axilla.netlify.app/?output=image)

## Axilla Query Parameters

_note: all query parameters are optional_

| Parameter | Default  | Description |
|-----------|----------|-------------|
| format    | `webp`   | Image format generated by Pixlet. `webp` or `gif` |
| output    | `html`   | Output type returned by the API. `html`, `image`, or `base64`|
| applet    | _AXILLA_ | URL of a Pixlet applet (which should be a [Starlark](https://github.com/bazelbuild/starlark) `.star` file.). Maximum file size 10MB. |
| pixelate  | `true`   | Set to `false` to disable pixelation simulation. _Note: This is only used when `output` is `html`._

### Special Parameters

_note: when present, other params are ignored and an applet is not executed_

| Parameter | Default     | Description |
|-----------|-------------|-------------|
| version   | `undefined` | When `true` returns Axilla and Pixlet version information as plain text. |

## Applet Query Parameters

Query parameters can be passed to Pixlet for use within an applet (i.e. `config.get('param')`). These parameters are defined by the applet itself. _Note: Axilla query parameters listed above are reserved and will not be passed to the applet._

## Examples

### All Defaults

[`axilla.netlify.app`](https://axilla.netlify.app)

### Raw GIF Image

[`format=gif&output=image`](https://axilla.netlify.app/?format=gif&output=image)

### Base 64 Image String

[`output=base64`](https://axilla.netlify.app/?output=base64)

### Other Parameters

The default Axilla applet accepts one parameter: `text`. Other applets can define and accept their own query parameters.

[`text=You%20Rock!`](https://axilla.netlify.app/?text=You%20Rock!)

### External Applets

#### Without App Parameters

- [`applet=https://raw.githubusercontent.com/tidbyt/pixlet/main/examples/hello_world.star`](https://axilla.netlify.app/?applet=https://raw.githubusercontent.com/tidbyt/pixlet/main/examples/hello_world.star)
- [`applet=https://raw.githubusercontent.com/tidbyt/pixlet/main/examples/clock.star`](https://axilla.netlify.app/?applet=https://raw.githubusercontent.com/tidbyt/pixlet/main/examples/clock.star)

#### With App Parameters

- [`applet=https://raw.githubusercontent.com/btjones/community/main/apps/flags/flags.star&show_name=true&country_code=us`](https://axilla.netlify.app/?applet=https://raw.githubusercontent.com/btjones/community/main/apps/flags/flags.star&show_name=true&country_code=us)
- [`applet=https://raw.githubusercontent.com/btjones/community/main/apps/randomslackmoji/random_slackmoji.star&query=dance`](https://axilla.netlify.app/?applet=https://raw.githubusercontent.com/btjones/community/main/apps/randomslackmoji/random_slackmoji.star&query=dance)

## Forking / Netlify Deployment

Axilla is deployed to [Netlify](https://www.netlify.com) and utilizes [Netlify Functions](https://www.netlify.com/products/functions/) (which uses [AWS Lambda](https://aws.amazon.com/lambda/) under the hood). To deploy your own version of Axilla:

1. Fork this repo (click Fork button on the top-right corner of this page)
2. [Link your forked repo to Netlify](https://www.netlify.com/blog/2016/09/29/a-step-by-step-guide-deploying-on-netlify/)
3. Visit https://YOUR-SITE-NAME.netlify.app/

## Local Development

1. [Install Netlify Dev](https://www.netlify.com/products/dev/)
2. [Install Pixlet](https://github.com/tidbyt/pixlet#getting-started)
3. Install Axilla dependencies:

        npm install

4. Launch Axilla locally:

        npm run dev

Note: When running locally, Axilla assumes you have Pixlet installed globally on your system and will use the `pixlet` command to execute. A version of Pixlet is included in this repo but has been built to run on the [Amazon Linux 2](https://aws.amazon.com/amazon-linux-2/) operating system so that it can run when deployed as a Netlify/Lambda function.

### Test

Run unit tests:

    npm run test

Run unit tests and watch for changes:

    npm run test:watch

## Pixlet

This application contains code from, and includes binaries of, [Pixlet](https://github.com/tidbyt/pixlet) which is covered under the [Apache License Version 2.0](PIXLET_LICENSE.txt).
