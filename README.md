![Version](https://img.shields.io/github/v/release/r3draid3r04/ha-blueprints)

# Home Assistant Voice Blueprints

## About this repository

On this respository I will put my blueprints which are created to help issuing advanced (voice) commands using Assist. 
There are basically 5 ways to configure a voice pipeline in Home Assistant:

|#|LLM|Home Control (Assist) enabled|Local preference enabled|Description|
|---|---|---|---|---|
|1|❌|NA|NA|Local only|
|2|✅|❌|❌|LLM as voice agent, no home control, no local preference|
|3|✅|❌|✅|LLM as voice agent, no home control, with local preference|
|4|✅|✅|❌|LLM as voice agent, with home control, no local preference|
|5|✅|✅|✅|LLM as voice agent, with home control, with local preference|

On this repository different blueprints will be placed with the same goal. The will differ in which op the above mentioned configurations are supported. Based on that, also other aspects will differ.

## Blueprint options

There are 3 options for the blueprints
* Option 1: Local automation
* Option 2: LLM Enhanced automation
* Option 3: Full LLM script

|Description|Option 1|Option 2|Option 3|
|---|---|---|---|
|Supported voice configurations|1, 2, 4|1, 3, 5|3, 4, 5|
|Fully local, no LLM required|✅|❌|❌|
|No home control for LLM required|✅|✅|❌|
|No strict voice commands|❌|✅|✅|
|Complete freedom in voice commands|❌|❌|✅|
|Variance in responses for each request|❌|✅|✅|
|Works without need for translations|❌|❌|✅|

The groundwork for option 2 was done by [JLo](<https://github.com/jlpouffier>) in his [blog post](<https://blog.jlpouffier.fr/chatgpt-powered-music-search-engine-on-a-local-voice-assistant/>) on GPT-powered music search. This blog post was a big inspiration for the LLM enhanced automation, and also enabled the full LLM script. So big thanks to JLo!

## The Blueprints

### 📰 News Headlines

These blueprints enable your Home Assistant to read news headlines to you through voice commands. The blueprints work with any RSS feed sensor, allowing you to get news from your preferred sources.

#### Prerequisites
- Install the [Feedparser integration](https://github.com/custom-components/feedparser) in your Home Assistant instance
- Configure an RSS feed sensor in your `configuration.yaml`

#### Example Configuration
Here's an example configuration using NPR News:

```yaml
sensor:
  - platform: feedparser
    name: NPR News
    feed_url: "https://feeds.npr.org/1001/rss.xml"
    date_format: "%a, %d %b %Y %H:%M:%S %Z"
    show_topn: 5
    scan_interval:
      hours: 3
    inclusions:
      - title
      - link
      - description
    exclusions:
      - language
```

You can customize this configuration to use any RSS feed of your choice. The blueprint will use this sensor to fetch and read the latest headlines.

|Option|Import Button|
|---|---|
|[1: Local](/documentation/news/1_voice_news_headlines_local.md)|[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fr3draid3r04%2Fha-blueprints%2Fblob%2Fmain%2Fnews%2F1_voice_news_headlines_local.yaml)|
|2: LLM Enhanced|To be created|
|[3: Full LLM](/documentation/news/3_voice_news_headlines_full_llm.md)|[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fr3draid3r04%2Fha-blueprints%2Fblob%2Fmain%2Fnews%2F3_voice_news_headlines_full_llm.yaml)|


## Planned

1. Think up more!

## Questions/issues/bugs/feature requests?

In case you have a question, you found a bug, or have a feature request open an [issue](https://github.com/r3draid3r04/ha-blueprints/issues) on this GitHub repository. 

In case something isn't working or you found a bug, a trace of the script will be needed in most cases to determine the cause. The trace can be downloaded as a json file. To do this follow the steps below:

1. Depending on the blueprint type go to [![Open your Home Assistant instance and show your scripts.](https://my.home-assistant.io/badges/scripts.svg)](https://my.home-assistant.io/redirect/scripts/) or [![Open your Home Assistant instance and show your scripts.](https://my.home-assistant.io/badges/automations.svg)](https://my.home-assistant.io/redirect/automations/)
2. Find the relevant script or automation in the list.
3. Click on 3 dot menu icon left of the script and then select `Traces`
4. Make sure to select the right trace which contains the error
5. Press the 3 dot menu icon in the top right corner, and select `Download trace`
6. Press the download icon in the top right corner.

In case you create the issue on GitHub you can upload the json files, in case you create the issue as a post here, you can copy the json files to a code sharing website like [dpaste.org](https://www.dpaste.org). Please create a different link for each json file.
