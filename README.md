# Sayvn 🔊 - "Say Maven" 
Sayvn is a Wrapper for Maven that notifies you via the OSX [`say`](https://ss64.com/osx/say.html) command, whether a task failed or succeeded.

# Why?
Knowing when a Maven build is done is super helpful when there are long running tasks.  This allows you to be notified instead of checking the terminal.

This is a port of [Sam Edwards](https://twitter.com/HandstandSam)' [Saydle](https://github.com/handstandsam/saydle/) wrapper for Gradle.

# System Requirements
* You must be Running Mac OSX

# Installation Instructions
Run the following command from the terminal in the root of your Maven Project (where the `mvnw` file is, if present):
```
curl -O "https://raw.githubusercontent.com/fbricon/sayvn/main/sayvnw" && chmod +x sayvnw
```

This will download the [`sayvnw`](https://github.com/fbricon/sayvn/blob/main/sayvnw) file and put it at the root of your Maven project. It then ensures there is permission to execute the file.

# Usage
* Instead of using `./mvnw`, `mvnd` or `mvn` , use `./sayvnw` instead.  That's it!
* Example: `./sayvnw clean verify`

# Advanced Configuration Options
You can edit these options in the `sayvnw` file itself.
* success_phrase="Success"
* failed_phrase="Failed"
* voice="Alex"

## Alternate Voices for the "say" Command
[OSX Say Command Documentation](https://ss64.com/osx/say.html)

**Available English Speaking Voices**
```
Alex                en_US    # Most people recognize me by my voice.
Fred                en_US    # I sure like being inside this fancy computer
Samantha            en_US    # Hello, my name is Samantha. I am an American-English voice.
Victoria            en_US    # Isn't it nice to have a computer that will talk to you?
```

**Other Languages**
Find other voices by running: `say -v '?'`

# How Does Sayvn 🔊 Work?

Sayvn 🔊 forwards your command to Maven, and then looks at the execution result to say either "Success" or "Failed". 

It will delegate the build execution to:
- `./mvnw`, the Maven Wrapper, if it's found in the current directory,
- `mvnd`, the Maven Daemon, if it's installed and available in the $PATH,
- `mvn`, the Maven Command Line Interface, if it's installed and available in the $PATH.
