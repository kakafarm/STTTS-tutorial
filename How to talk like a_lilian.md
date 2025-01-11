# How to talk like a_lilian

Beep boop, hello there, I am a_lilian! 

I am a streamer who talks using speech-to-text-to-speech (STTTS). This means I say words out loud into a microphone which are transcribed into text (STT) and then synthesized back into speech using a text-to-speech model (TTS). I do this because I find speaking [difficult], and because I find TTS a meaningful medium for [self expression]. 

I hope that this guide will help you to speak like I do. 

I currently use Windows 10 and I'll try my best not to have an autistic meltdown when it's time to upgrade to 11 🫠

## Curses

There are several STTTS platforms but the one I use is called Curses. Curses was created by [Mmp](https://www.patreon.com/c/mmpcode). The main branch of Curses can be found [here](https://github.com/mmpneo/curses). [zqlk's branch](https://github.com/zqlk256/curses) of Curses adds Piper as a TTS service. A pull request to merge zqlk's branch into the main branch is pending, but I haven't been able to reach Mmp in quite a while. 

You can download either version from their respective **releases** links:

- [Main branch releases](https://github.com/mmpneo/curses/releases)
- [zqlk's branch releases](https://github.com/zqlk256/curses/releases)

## Security Warnings

When you try to download and run Curses for the first time, Windows will present you with security warnings. You will need to decide for yourself whether you feel safe allowing the Curses executable to run on your computer. 

Open source software can theoretically be safer because anyone can review the code for malicious components, but I do not have the expertise to do that. Do you trust Mmp to write code you run on your computer? Do you trust zqlk?

## Speech-to-Text (STT)

The first half of STTTS! This is where Curses takes your microphone input and transcribes the things you say into text. I've only ever used the Native service which captures the system default microphone. The other options may give you more flexibility with profanity, but I like how Cori mutters _asteriskasteriskasterisk_ under their breath when I swear. 

You may want to test that words get transcribed when you speak into your microphone before moving on to the next step. Don't forget to press the **Start** button!

You can also skip this part and type words into the textbox directly.

## Text-to-Speech (TTS)

The second half of STTTS! This is where Curses takes the words it transcribes and sends them to a voice model to be said out loud.

At the moment, the main branch of Curses integrates with several services: Windows/Native, Azure, TikTok, and Uberduck. ZQLK's branch adds Piper as an additional option. You can choose which service you want to use from the **Service** drop-down.
 
### Windows/Native

This is your Windows computer's native speech synthesis that is most commonly used in accessibility contexts. Microsoft Zira and David come installed by default on US installations. You can read about downloading and installing different localized voices and languages [here](https://support.microsoft.com/en-us/windows/appendix-a-supported-languages-and-voices-4486e345-7730-53da-fcfe-55cc64300f01#WindowsVersion=Windows_10).

The native voices are fast, free, and local, meaning that they will run without any fuss without an internet connection. They come from an earlier era of speech synthesis that came before neural models, meaning that they have a characteristic robotic, buzzy sound. 

Voices like these have a rich history of use in screen readers and creative projects. I find them timeless, austere, and beautiful, and I'll be sad if they get swept away just because newer models sound more "natural."

### Azure

Azure is Microsoft's cloud service platform which provides a TTS service as one of its many offerings. To use Azure with Curses, you will need to make an Azure account, configure a payment service, configure a speech service, and then enter your API key into Curses. Do not share your API key. Doing so would allow someone to use your Azure service at your expense.

Cloud service platforms like Azure and Amazon Web Services are catered to businesses so the backend can be dense and inaccessible to an inexperienced user. Being a cloud service, the computational demand of running the models is offloaded onto Azure's servers. Of course, that subjects you to latency and reliability issues, and Azure will charge you money for providing this service.

I find the Azure neural voice models to be clear, clean, and more natural sounding while still being clearly identifiable as a TTS voice. 

### TikTok/Uberduck

I don't use TikTok and I don't know what Uberduck is. Are all these TikTok voices memes? I have no idea! 

One thing to be thoughtful about is that any time you use a cloud service (including Azure), you are likely providing explicit or implicit consent to their Terms of Service and Privacy Policy. Are you comfortable with TikTok's Privacy Policy governing the TTS half of your STTTS configuration?

## Piper

Uhoh. There's so much going on in the Piper section that I broke the header hierarchy! 

Piper is a free and open source command line tool for creating and running neural voice models. It will only show up as an option if you've downloaded ZQLK's branch of Curses.

Piper and its models run locally on your computer.

To use Piper with Curses, you will need to download the Windows release of Piper and a Piper voice model. You will then enter the paths to these files in Curses so Curses can find and use them.

### The Windows Release of Piper

Piper releases can be found [here](https://github.com/rhasspy/piper/releases). At the time of writing this, the most recent Windows release and the one I use is the **2023.11.14-2** release. To use it, you will need to download the `piper_windows_amd64.zip`file and extract the folder to somewhere on your hard drive. 

Curses will need the path to the `piper.exe` executable file in this folder, for example `C:\users\lilian\piper\piper.exe`.

Oh dear, it's another executable downloaded from the internet! Do you trust the Piper team too? 

### The Piper Voice Model

Each Piper voice model comes in two files: one that ends in `.onyx` and one that ends in `.json`. The `.json` file has some parameters that can be adjusted to change aspects of the voice like how fast it speaks.

Curses will need a path to the file where these files are stored on your hard drive, for example `C:\users\lilian\piper\voices`. Then you will click **Scan Directory** to tell Curses to index the voice models in this file.

When scanning, Curses is looking for a pair of`.onyx` and `.json` files with the same name before the `.`. If you have your files saved as `en_GB-cori-medium.onyx` and `cori.json`, it won't work and you can end up going on a wild goose chase trying to troubleshoot something unrelated. Ask me how I know ಠ_ಠ

One aspect of Piper models to be aware of is their licenses. Some of them are public domain like Cori. Others may have restrictions or require some kind of attribution, like the one trained on the [Jenny (Dioco) dataset](https://github.com/dioco-group/jenny-tts-dataset).  

## Outputting Your Voice to Another Program

Ah, this is the part I find myself helping people with the most! Curses lets you set an output device so it's pretty easy to get the voice playing in your headphones, but how do you get it to play through Discord or VRChat? 

The piece you're missing is a virtual audio cable. You need something that Curses can use as an input and Discord (or another program) can use as an output. I've always used [VB-Audio](https://vb-audio.com/Voicemeeter/index.htm) software for these kinds of things but feel free to go with whatever works for you. And oh dear, we are once again downloading and installing programs off the internet ... be careful!

A plain virtual audio cable should work fine to pipe Curses' sounds to Discord or a game, but I actually use [Voicemeeter](https://vb-audio.com/Voicemeeter/index.htm) because it lets me play the audio to the game and to my headphones at the same time so I hear my voice at the same time everyone else does! It helps me catch mistakes and I also find it soothing to listen to. 

## Good luck! 

I hope it works out well for you! There's a lot of computer-y setup steps so please be patient with yourself if things don't work on the first try. There's nothing wrong with asking for help if you need it.

[airplane]
