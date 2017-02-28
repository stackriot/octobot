---
layout: page
permalink: /
order: 0
headings:
    - title: Motivation
    - title: Requirements
    - title: Installation
    - title: Getting Help
---

So you want to get started with ChatOps using Hubot and Slack? We've got you covered. {{ site.product_name }} is an
adapter that connects your Hubot scripts to your Slack team, giving you and your fellow DevOps engineers a new best friend: your very own ChatOps bot.

## Requirements and Installation

Of course, you'll need Node.js, as well as NPM. NPM has
[a great tutorial](https://docs.npmjs.com/getting-started/installing-node) to help you get started if you don't have
these tools installed. [Yeoman](http://yeoman.io) is also a great tool for getting started on your first Hubot.

To install, you will first want to create a new Hubot project. The simplest way is to use your computer's terminal app
to invoke Yeoman.

```bash
npm install -g yo generator-hubot
```

This will install the Yeoman Hubot generator. Now we can create that Hubot project:

```bash
mkdir my-awesome-hubot && cd my-awesome-hubot
yo hubot --adapter=slack
```

This script will prompt you to describe the app you are going to build, and create a file that NPM can use to help
manage your project.

You will also need to set up a Custom Bot on your Slack team. This will create a token that your hubot can use to
log into your team as a bot. Visit the [Custom Bot creation page](https://my.slack.com/apps/A0F7YS25R-bots) to register
your bot with your Slack team, and to retrieve a new bot token

## Running Hubot

Once you've got your bot set up as you like, you can run your hubot with the run script included (being sure to
copy-and-paste your token in!):

```bash
HUBOT_SLACK_TOKEN=xoxb-YOUR-TOKEN-HERE ./bin/hubot --adapter slack
```

## Getting Help

If you get stuck, we're here to help. The following are the best ways to get assistance working through your issue:

  * [Issue Tracker](http://github.com/slackapi/{{ site.repo_name }}/issues) for reporting bugs or requesting features.
  * [dev4slack channel](https://dev4slack.slack.com/archives/{{ site.dev4slack_channel }}) for getting help using
  {{ site.product_name }} or just generally commiserating with your fellow developers.
=======
title: Hubot
permalink: /docs/index.html
layout: docs
---

## Getting Started With Hubot

You will need [node.js and npm](https://docs.npmjs.com/getting-started/installing-node). Once those are installed, we can install the hubot generator:

    %  npm install -g yo generator-hubot

This will give us the `hubot` [yeoman](http://yeoman.io/) generator. Now we
can make a new directory, and generate a new instance of hubot in it. For example, if
we wanted to make a bot called myhubot:


    % mkdir myhubot
    % cd myhubot
    % yo hubot

At this point, you'll be asked a few questions about who is creating the bot,
and which [adapter](/docs/adapters.md) you'll be using. Adapters are hubot's
way of integrating with different chat providers.

If you are using git, the generated directory includes a .gitignore, so you can
initialize and add everything:

    % git init
    % git add .
    % git commit -m "Initial commit"

If you'd prefer to automate your hubot build without being interactively
prompted for its configuration, you can add the following options
to the `yo hubot` command to do so:

| Option                                      | Description
| ------------------------------------------- | -----------------------------------------------------
| `--owner="Bot Wrangler <bw@example.com>"`   | Bot owner, e.g. "Bot Wrangler <bw@example.com>"
| `--name="Hubot"`                            | Bot name, e.g. "Hubot"
| `--description="Delightfully aware robutt"` | Bot description, e.g. "Delightfully aware robutt"
| `--adapter=campfire`                        | Bot adapter, e.g. "campfire"
| `--defaults`                                | Declare all defaults are set and no prompting required

You now have your own functional hubot! There's a `bin/hubot`
command for convenience, to handle installing npm dependencies, loading scripts,
and then launching your hubot.

Hubot needs Redis to persist data, so before you can start hubot on your own computer, you should have Redis installed on your localhost. If just want to test Hubot without Redis, then you can remove `hubot-redis-brain` from `external-scripts.json`.

    % bin/hubot
    Hubot>

This starts hubot using the [shell adapter](/docs/adapters/shell.md), which
is mostly useful for development. Make note of  `Hubot>`; this is the name your hubot will
`respond` to with commands. For example, to list available commands:

    % bin/hubot
    hubot> hubot help
    hubot adapter - Reply with the adapter
    hubot animate me <query> - The same thing as `image me`, except adds a few parameters to try to return an animated GIF instead.
    hubot echo <text> - Reply back with <text>
    hubot help - Displays all of the help commands that hubot knows about.
    hubot help <query> - Displays all help commands that match <query>.
    hubot image me <query> - The Original. Queries Google Images for <query> and returns a random top result.
    hubot map me <query> - Returns a map view of the area returned by `query`.
    hubot mustache me <query> - Searches Google Images for the specified query and mustaches it.
    hubot mustache me <url> - Adds a mustache to the specified URL.
    hubot ping - Reply with pong
    hubot pronounce <phrase> in <language> - Provides pronunciation of <phrase> (<language> is optional)
    hubot pug bomb N - get N pugs
    hubot pug me - Receive a pug
    hubot the rules - Make sure hubot still knows the rules.
    hubot time - Reply with current time
    hubot translate me <phrase> - Searches for a translation for the <phrase> and then prints that bad boy out.
    hubot translate me from <source> into <target> <phrase> - Translates <phrase> from <source> into <target>. Both <source> and <target> are optional
    hubot youtube me <query> - Searches YouTube for the query and returns the video embed link.
    ship it - Display a motivation squirrel

You almost definitely will want to change your hubot's name to add character. bin/hubot takes a `--name`:

    % bin/hubot --name myhubot
    myhubot>

Your hubot will now respond as `myhubot`. This is
case-insensitive, and can be prefixed with `@` or suffixed with `:`. These are equivalent:

    MYHUBOT help
    myhubot help
    @myhubot help
    myhubot: help

## Scripts

Hubot's power comes through scripts. There are hundreds of scripts written and maintained by the community. Find them by searching the [NPM registry](https://www.npmjs.com/browse/keyword/hubot-scripts) for `hubot-scripts <your-search-term>`. For example:

```
$ npm search hubot-scripts github
NAME                  DESCRIPTION
hubot-deployer        Giving Hubot the ability to deploy GitHub repos to PaaS providers hubot hubot-scripts hubot-gith
hubot-gh-release-pr   A hubot script to create GitHub's PR for release
hubot-github          Giving Hubot the ability to be a vital member of your github organization
…
```

To use a script from an NPM package:

1. Run `npm install --save <package-name>` to add the package as a dependency and install it.
2. Add the package to `external-scripts.json`.
3. Run `npm home <package-name>` to open a browser window for the homepage of the script, where you can find more information about configuring and installing the script.

You can also put your own scripts under the `scripts/` directory. All scripts placed there are automatically loaded and ready to use with your hubot. Read more about customizing hubot by [writing your own scripts](/docs/scripting.md).

## Adapters

Hubot uses the adapter pattern to support multiple chat-backends. Here is a [list of available adapters](/docs/adapters.md), along with details on how to configure them.

## Deploying

You can deploy hubot to Heroku, which is the officially supported method.
Additionally you are able to deploy hubot to a UNIX-like system or Windows.
Please note the support for deploying to Windows isn't officially supported.

* [Deploying Hubot onto Heroku](/docs/deploying/heroku.md)
* [Deploying Hubot onto UNIX](/docs/deploying/unix.md)
* [Deploying Hubot onto Windows](/docs/deploying/windows.md)

## Patterns

Using custom scripts, you can quickly customize Hubot to be the most life embettering robot he or she can be. Read [docs/patterns.md](/docs/patterns.md) for some nifty tricks that may come in handy as you teach your hubot new skills.
