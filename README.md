# Are They Asleep?

Check a teammate's timezone and see if they're awake!

 ![Badge](https://github.com/shundor/are-they-asleep/workflows/test/badge.svg) [![code style: prettier](https://img.shields.io/badge/code_style-prettier-ff69b4.svg?style=flat-square)](https://github.com/prettier/prettier)

## About

This action allows you to check a teammate's timezone via an issue or PR comment.

## Usage

Create a workflow like the following:

```yaml
name: Example Workflow

on:
  issue_comment:
    types: [created, edited]
    branches:
      - main     
jobs:
  comment:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v3
      - name: Check if teammate is awake?
        id: are-they-asleep
        uses: shundor/are-they-asleep@v1.0.0
        env:
          GITHUB_TOKEN: "${{ secrets.GITHUB_TOKEN }}"
          GOOGLE_API_KEY: "${{ secrets.GOOGLE_API_KEY }}"          
```
Then, in your issue or PR, add this comment:

```text
    is @teammate awake?
```
`@teammate` being the remote teammate you want to check.
## Inputs

The following [secret](https://docs.github.com/en/actions/security-guides/encrypted-secrets) needs to be created:

- `GOOGLE_API_KEY`: The Google Cloud API Key

The following [Google Map Platform](https://console.cloud.google.com/google/maps-apis/overview) API's need to be enabled, and the API should be restricted to them:

- Geocoding API
- Geolocation API
- Maps JavaScript API
- Time Zone API

For this action to work correctly the team must have their location set in their [GitHub Profile](https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-github-profile/customizing-your-profile/personalizing-your-profile#setting-your-location-and-time-zone).

## Outputs

If successful, the issue will have a new comment with the teammate's timezone info:

```text
    Hi there, abirismyname! 👋
    

    You asked if rufusmbugua was awake yet.

    I can't tell you about their personal sleeping habits, sadly.

    I can tell you though that the date and time for rufusmbugua in Nairobi, Kenya is currently:

    December 29th 2022, 7:28 pm

    I hope that helps clarify the matter for you!
```

## Example

This repo contains an example [workflow](https://github.com/shundor/awake-yet-action-js/blob/main/.github/workflows/example.yml) that contains this action.

## Credits

- :bow: Based on [bencgreenberg/awake-yet-action](https://github.com/bencgreenberg/awake-yet-action).
- :bow: [@breton](breton) for the testing and help!
- :bow: [@manishapriya94](manishapriya94) for inspiration!
