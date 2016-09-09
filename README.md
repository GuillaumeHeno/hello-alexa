

# Prerequisites

* Install Node.js and update npm (v. 5 or later) using these instructions: https://docs.npmjs.com/getting-started/installing-node

* You will need an AWS account; the [free tier](https://aws.amazon.com/free/) is sufficient for this lesson.

* You will also need to register as a developer in [Amazon's developer portal](https://developer.amazon.com/).

## Setting up your skill

With all the prerequisites in place, you're ready to define your skill. There are several steps in this process. First, log into the [Amazon Developer Portal](https://developer.amazon.com), and then click the Alexa link at the top of the page. You'll be prompted to choose a starting point (Alexa Skills Kit or Alexa Voice Service). Click Get Started under the Alexa Skills Kit option:

<img src="images/alexa-skills-portal.png" width="100%"/>


<!-- https://developer.amazon.com/alexa takes me to a landing page where I need to sign in, and I still need to click the Alexa link. https://developer.amazon.com/edw/home.html is a direct link that works, but with a name like /edw, I'm not sure if that URL is a reliable permalink. -->

### Step 1: Add the New Skill

* Click the Add a New Skill button

In this step, you'll define the basic characteristics of the skill: its name, the name that people use to invoke it, and a couple of other settings.

<img src="images/add-new-skill.png" width="100%"/>

* Set the following options:
  * Skill type: Make sure this is set to Custom Interaction Model.
  * Name: This is what appears in the Alexa app. Call it "Tide Pooler."
  * Invocation Name: This is how users will activate the skill. Use "Tide Pooler" here as well.
  * Audio Player: You can leave this set to No for this skill. If you were playing audio, such a music, that you wanted to allow users to stop or pause, you'd need this. You won't need it here.
* Click Next.

<img src="images/set-skill-information.png" width="100%"/>


### Step 2: Define the Skill's Interaction Model

Now you're in the Interaction Model section of the setup process. This is where you describe what sorts of things you can say to the skill. The first part is the _intent schema_, which defines the _intents_, or kinds of interactions your skill has. A given intent  corresponds to a function that you'll define later; it will look up tide info, format it into a nice result, and that will be read back to the user. The second part is a collection of utterances, and they are (mostly) human-readable sentences with optional _slots_ for one or more parameters. Not all skills will need a parameter, but Tide Pooler needs to know what city the user is curious about.

NOTE: You can also copy this schema from this Lesson's [GitHub repository](https://github.com/oreillymedia/hello-alexa/blob/master/config/intents.json).

Put the following schema into the Intent Schema. The first intent is _GetTideIntent_, which is the intent for asking about the high tide. The other intents allow users to ask the skill for help, or to stop or cancel it.

    {
      "intents": [
        {
          "intent": "GetTideIntent",
          "slots": [
            {
              "name": "City",
              "type": "AMAZON.US_CITY"
            }
          ]
        },
        {
          "intent": "AMAZON.HelpIntent"
        },
        {
          "intent": "AMAZON.StopIntent"
        },
        {
          "intent": "AMAZON.CancelIntent"
        }
      ]
    }

Now you're ready to get into the actual things you can ask the skill. Put the following text into the Sample Utterances field. Note how each utterance refers to the City slot:

    GetTideIntent when is high tide in {City}
    GetTideIntent when will it be high tide in {City}
    GetTideIntent what time is high tide for {City}
    GetTideIntent what time is high tide in {City}

NOTE: You can also copy the list of utterances from this Lesson's [GitHub repository](https://github.com/oreillymedia/hello-alexa/blob/master/config/utterances.txt).

The GetTideIntent signifies that the user wants to know when high tide is. They can ask it in several ways:

* When is high tide in Newport, Rhode Island?
* When will it be high tide in New Bedford, Massachusetts?
* What time is high tide for Gloucester, Massachusetts?
* What time is high tide in Gloucester, Massachusetts?

Because this skill is only using the built-in `AMAZON.US_CITY` slot type, you won't need to define any Custom Slot Types.

Click Next, and you'll move on to the Configuration step.

###

# Getting started

* Clone this repository
* run `npm install`

# Setting up your keys

Create a file called `.env` to store all the various keys you'll need, like this:

```
AWS_KEY=<your aws key>
APP_ID=<your app id>
```

In your program, you'll refer to these as `process.env.AWS_KEY`, `process.env.APP_ID`, etc.  

Note that we add the `.env` to `.gitignore` so that you don't accidentally check your keys into your github repo, which would be bad!
