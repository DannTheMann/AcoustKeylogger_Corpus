<div style="position:fixed; top:0; left:0; margin:10px;">
<a href="#contents">Back to Contents</a>
</div>

# Acoustic Keylogging via Smartphone devices - Corpus

## Contents

1. **Introduction**

   * Author & date
   * Abstract and Aim
   * Special Thanks

2. **Meetings**

   * Purpose


   * Audio files
   * Meeting summaries

3. **Previous Research**

   * Accelerometer Side Channel Attacks
   * Cracking Passwords using keyboard acoustics and language modelling
   * Keyboard Acoustic Emanations
   * Keyboard Acoustic Emanations Revisited
   * Electronic emanations of wired and wireless keyboards

4. **Hardware**

   * Smartphone Technology
     * Microphone
   * The Android Operating System
     * Android 'Java'
   * Keyboard Hardware

5. **Testing conditions**

   * Constraints
     * Keyboard 
       * Location
       * Membrane vs Mechanical 
     * Smartphone 
       * Operating System 
       * Microphone
     * Lab conditions
   * Variables
     * Background noise
     * Phone model
     * Location of phone
     * Keyboard 

6. **Testing methodology**

   * Initial testing plans
   * Testing process
     * Small subset
     * Larger subset

7. **Feature extraction**

   * Features
     * Amplitude
     * Frequency
   * Pre-recorded audio extraction
   * Live audio extraction 
   * Isolating peaks
     * Subsampling

8. **Feature Analysis**

   * Simple comparison
   * Supervised and unsupervised learning
     * Mean approximation 
     * Kmeans clustering
   * ​

9. **Development process**

   * Development process ideology
     * Iterative design
     * Version control
     * IDE (Integrated Development Environment)
   * Program functionality
     * Learning capabilities
     * Data management
     * Visualisation
   * Program Steps
     * Initial Setup
       * Launch
       * GUI building
       * Dataset loading
       * Thread establishment
     * Feature Extraction
     * Feature Analysis
     * Supervised/Unsupervised Learning
       * Mean approximation
       * Kmeans clustering
         * 1 dimensional
         * 2 dimensional
     * Storing results
   * Android API
     * API Permissions
     * AudioRecord
     * Thread management
     * XML Design Layouts
   * Storage facilities
     * Internal and External Storage
     * Serialisation
     * Exporting and importing datasets
   * GUI functionality
     * Buttons
     * Visualising

10. **Results**

   * Initial results
   * Using sophisticated feature extraction
   * Mean approximation
   * Kmeans clustering
   * Cryptographic substitution frequency analysis

---

## 1. Introduction

###1.1 Author & Date

This project was started in January of 2017 and finished in August of 2017, with the current dated version of this corpus being 21/8/2017.

The author of this corpus is Daniel Jack Andrews, if you have any queries you can contact the author at [dja33@kent.ac.uk](mailto:dja33@kent.ac.uk).

### 1.2 Abstract & Aim

#### 1.2.1 Abstract

Nearly every user on the market owns a smartphone within the western first world. These modern day smartphones often contain technology that is more powerful and sophisticated that the rockets that delivered man to the moon.

Considering this the potential power behind the average smartphone is huge, even for the purpose of breaking security measures. Computer keyboards are not a new invention and have been rooted to the development of computers since their creation; however they are fundamentally at the hand of every and all sensitive data entry. Sensitive data could reflect bank details, passwords, personal or confidential information and more. 

The dissertation that this corpus supports aims to challenge whether a modern day smartphone can acoustically eavesdrop on a keyboard through side-channels in the acoustic noise produced by pressing the keys on the board.

#### 1.2.2 Aim

This corpus aims to provide and support the dissertation associated with it such that any reference of relation to the material, results or development of the dissertations logic, applicants or findings can be backed up and catalogued. This corpus will skim over certain aspects of the project, where instead these details can be found in the bulk of the dissertation. Instead this corpus aims to provide a uniformed catalogue of data used as referencing points in the dissertation thesis itself.

### 1.3 Special Thanks

This project could not have been completed without the following people and groups who have provided wonderful guidance and support throughout the project.

* Budi Arief - Supervisor, computer security lecturer.
  * Met with me regularly to conduct guidance meetings and help keep me on track of the topic at hand, always firm and willing to provide assistance when needed.
  * Founded the project concept and passed it onto me.
* Samuel Williams - PhD candidate, programming language implementation specialist.
  * Provided fantastic knowledge on artificial intelligence and had a deep appreciation for the research topic covered in this material.
* Alice Mo - Data Mining Analyst and MSc candidate at University College London
  * Fundamentally showed and helped deal with resolving data and identifying useful traits in it.
* Michael Berry - PhD, software engineer, electronics tinkerer and radio licence holder.
  * Provided assistance on digital signal processing, explaining Fourier transforms and utilising feature extraction.
* The Shed - Group of knowledgeable technicians with a wealth background experience in varying fields.
  * Helped laser cutting a frame and suggesting potential fixes to issues.

---

## 2. Meetings

### 2.1 Purpose

On several occasions I met my supervisor Budi Arief to discuss the project undertaken. These meetings were intended to provide insight into the current status of the project while assisting in any issues and providing other forms of support to the project.

### 2.2 Audio recordings

Unfortunately I have only three audio recorded sessions as my audio recording equipment failed on two occasions. Below are the three recorded meetings I do have access to. For all other meetings I took detailed notes on our discussions.

* 15/5/2017 (In person) - [View](meetings_audio/15.05.m4a)
* 21/7/2017 (In person) - [View](meetings_audio/21.07.m4a)
* 14/8/2017 (On Skype) - [View](https://youtu.be/ac2mPSi0TXU)

In-between June and August I lost two of my recordings. 

### 2.3 Meeting summaries

##### 31/1/2017 - Initial Preparation

Discussed hardware capabilities, such as whether the phone being used has multiple microphones, where they are and what sort of sensors to utilise.

Discussed controlled environment settings:

- Specific keyboard to use, in this case mechanical keyboard model "Razer BlackWidow 2014 Ultimate" - using Razers patterned mechanical keys.
- Specific to Android OS only for the purpose of the research
- 20 presses of specific keys, 'Q', 'W', etc.
- Lasercut potential frame to hold keyboard and phone, ensure that the distance between them is always fixed and therefore stops variations in this.
- Decided to use my Android phone to do this project under.
- Keys such as space will be hard to identify due to their size and potential to be struck in varying places.

Other items to note:

- Research into Side-Channel attacks, use Google scholar or the similar academic search engine.
- Pattern databases.
- Look into Accelerometer feature set and how it interacts with the Android OS.
- Record the results of whatever happens.

##### 17/2/2017 - Measuring Raw Data

- Produced a small demo Application for Android that will report sensory data from the phone, discussed which keys to focus on and just recording the values for the time being before trying to identify any particular pattern.
- Use keys that are of varying sizes and distances away from one another to help for identification, keys mention included:
  - Q
  - ENTER
  - SLASH
  - W
  - H
  - SPACE
- Investigate potentially new technologies
- Research into feature extraction to further develop an understanding of the topic material
  - For sound:
    - Amplitude
    - Frequency (Fast Fourier Transform, algorithm adapted from discrete fourier transform)
  - For accelerometer:
    - X, Y, Z forces
    - Speed
    - Also capable of performing FFT on these as well
  - Alternatively, potential for Gyroscopic sensor too.

##### 28/2/2017 - Initial Attempt at Isolating Raw Data

Initially this was a demoralising iteration, I found that the accelerometer was slow within the Android SDK and that I would not reliable be able to identify or determine key presses given such little ranging values over a sample, such that I decided for the time being to focus solely on acoustic keylogging rather other features. 

Decided to go back to the 'drawing' board and look at research more thoroughly, other assessments had gotten in my way and little work had been made through this iteration.

Had difficulties isolating the memory storage on the Smartphone as it appeared under a 'virtual' filesystem such that I couldn't accurately locate the file that I was saving all my samples and readings to.

Found that amplitude wasn't a good measurement for feature extraction alone and that frequency would be an absolute requirement.

Had laser cut a frame however to hold the phone and keyboard in place.

##### March, April, May

A lot of this time was spent working on assessments, exams and job interviews. Evaluation of research was the focus in this period while the development occurred post June. As such I shall present the researched papers and a link to my evaluations of those. These papers provided the foundation of the majority of my work, with research from Andrew Kelly featuring prominently.

* Cracking Passwords using keyboard Acoustics and Language Modeling - Andrew Kelly (2010)
* Keyboard Acoustic Emanations - Asonov and Agrawal (2004)
* Keyboard Acoustic Emanations Revisited - Zhang, Feng, Tygar (2009)

##### 15/06/2017 - Pre deliverable submission

[Audio](meetings_audio/15.05.m4a)

We discussed what had been completed so far for the project, I had scrapped my previous codebase as I wasn't happy with the quality of it. As such the focus at this part was that the research had been fully conducted in the project. 

We focused on three main elements of the project after research:

* Experimentation and methodology
  * Consistent testing
  * A lab condition
  * Training data sets on keypresses
* Implementing a proof of concept
  * On the Android operating system
  * Focussing on live-recorded audio
  * Some form of machine learning involved
* Other ideas for later use
  * Dictionary based attack to decipher potentially misspelled English words
  * Potential to then get the context behind a message, the emotion and power play of the words
  * Biometric profile of the individual

##### 6/07/2017 - Implementation progress update

Unfortunately I lost the recording for this meeting but I did however make some notes on the topics mentioned. The focus of the meeting was applying a Fourier transform across a discrete dataset of values for analysis in the frequency domain. Such that we could later pass this into a feature extraction function that would return us distinct features of keystrokes.

##### 12/07/2017 - Implementation progress update

Another lost audio recording for this meeting.

I had successfully written a feature extraction algorithm that was able to identify distinct differences in frequency and magnitude between two key presses, albeit there were complications with live audio recording as to be expected.

The next focus on was on refining this feature extraction if possible and looking into a primitive machine learning algorithm to help classify and train the keys being pressed. In this case the focus being on a supervised algorithm.

##### 21/7/2017 - Testing methodologies 

[Audio](meetings_audio/21.07.m4a)

A setback  occurred where my AudioRecord API ceased to operate and instead started spurring errors, after fixing these owing to updated Android API permission system the project was back on track.

Discussed the possibility of focussing on multiple keyboards but for the time being decided to look at just one keyboard until later period. Talked about storing the data and dealing with Androids file system in a manner that can be adjusted accordingly if need be. Java offers serialisation, a useful mechanism of preserving the data encapsulated within an object at runtime; potential for this tool to be used. Preserving data comes in the form of being able to then use this as a measurement of comparison for later, i.e I'm able to identify the key C because I have told my program from training that key C sounds like this.

Decided that the phone should handle everything, previously there was a thought of potentially having a machine elsewhere decode the live audio into information but instead the confirmation of the phone being the sole processing machine was decided. Rationality for this was user ability, if anyone owns a phone then they also can do what this project aims for.

Discussed potentially having a visual display of characters being decoded as an end goal, however for this to be effective it would require that the device was able to quickly identify as many keys as possible as well as having a high degree of accuracy in doing so.

Talked briefly about Mel-cepstrum Frequency Analysis, a technique often used in voice recognition systems although this methodology was too foreign to be adopted. 

Finished up with discussing the corpus and dissertation display and layout, decided to use markdown and provide the corpus in a HTML relative structure.

##### 14/8/2017 (On Skype) - Evaluation of Android Application 

[Audio](https://youtu.be/ac2mPSi0TXU) - Provided on YouTube, otherwise it's 1.4GB.

**Note** - The previous 3 weeks consisted of back and forth between me and Budi, trying to arrange a meeting as both of us were unavailable at several periods. 

This meeting was a final conclusive meeting of the project coming to an end. I spent time explaining the working system for the keylogger as well as providing details on several anecdotes regarding the system. Details included:

* Feature extraction
* Mean average supervised learning
* Kmeans unsupervised learning
* Saving results
* Identifying keystrokes based on results

The he results of kmeans clustering were more accurate than mean average, kmeans scored around ~60% while mean average scored around ~52%. At this point the focus was on writing the corpus and working towards the dissertation. 

**Note** - A final meeting is planned for the 29/8/2017 but since the Corpus will have been submitted it will not be documented, this meeting aims to provide details and feedback on the state of the dissertation.

---

## 3. Research

### 3.1 Accelerometer Side Channel Attacks

[Paper](research/AccelerometerSideChannel.pdf)

Using the accelerometer on Android based smartphones to determine a users phone pin/pattern unlocking code. Research in this field shows that success rates in controlled environments are high (such as the user sitting down being motionless) whereas in uncontrolled environments rates dropped but still maintained a concerning high level of accuracy.

They provided relevant research from others in the field in similar veins of collecting data, previous papers referenced in this include:

- [TouchLogger](research/TouchLogger.pdf): Inferring Keystrokes On Touch Screen From Smartphone Motion
- [TapPrints](research/TapPrints.pdf): Your Finger Taps Have Fingerprints - focuses on a similar vein of research as the source but utilises gyroscopic and accelerometer data to infer key presses.

The paper makes reference to different MAXIMUM sample rates of certain phones and through my own research I've found a piece of [software](https://github.com/dantasse/AccelerometerTest/) capable of measuring the speed of a phones accelerometer which will be useful later in my own research.

They used multiple phones to correlate their findings with varying refresh rates. Collected 5 samples of each pin/pattern entry but before this had each tester enter 50 random pins/patterns with their dominant hand then following this doing the same but walking around.

- The controlled data (Sitting) was used for training.
- The variable data (Walking) was used for testing.
- Utilising multiple mathematical formula to try to classify the data in a meaningful manner.
  - Mean Normalisation, Linear Normalisation, Quadratic Normalisation
  - iFFT-Poly, iFFT-Acc and 3D-Polynominal graphing

Utilising these formula they found a large **variance** between values, even when entering the same pin and such that they needed to **normalise** the raw signal. They used a 1-dimensional Discrete Fourier Transform with a resolution of 35 samples and found that the larger sample set would add to much variance while a smaller sample set would not preserve enough information.

The paper talks in detail about using Hidden Markov Models to predict unknown pins due to the limitations of having a classifier that only knows the patterns given by users.

They then suggest potential solutions to the problem presented:

- Vet programs that use sensors, try to identify any malicious behaviour or intent. Scale is too hard for this.
- Restrict sampling rate, but as the paper demonstrates even at 20KHz still possible to monitor fairly accurately.
- Utilise a permission model warning users about the permissions given to an app, mostly ignored by the user anyway.

Their suggested solution is:

- Disable the sensors whenever a trust related action is being performed, such as entering a password. Current security models do not allow for this, but future proofing may be required.

**Conclusion**

Conclusively the paper ends by explaining that a side-channel attack is possible and potentially dangerous even with noise introduced, drawing parallels between itself and other papers in the field it makes use to explain how one could expand upon the research. 

However this research focuses on inferring data from then touchscreen and does not guarantee that the same can be used for keystrokes on a physical keyboard. (As it later turns out, this is the true that Android is too limited to be able to deduce another features alone from vibrations for keystroke analysis)

###3.2 Keyboard Acoustic Emanations 

[Paper](research/KeyboardAcousticEmanations.pdf)

Written in 2004 the original paper addresses the ability to identify with a high degree of accuracy keystrokes from emanations created from sound via side-channel attacks. Asonov and Agrawal provide a detailed understanding of the attack, how it works, why it works and methods to potentially disable or weaken the attack.

The paper expands by explaining that they recorded 2-3ms worth of the ’touch-peak’ in which they are able to extract reliable features from the sample given. That initially they tested keys ’l’ and ’k’ individually 100
times and then fed the results as a key-value pair into an neural network. The neural network was then able to identify each key press of ’l’ and ’k’ with a given 100% accuracy, however this initial experiment was at a
performance of 1 metre with a microphone that may potentially exceed the capabilities of the Samsung S4s microphone. Later they experimented with variable distances and background noise with just keys ’l’ and ’k’ to challenge the accuracy of the neural network; with a distance of up to 15 metres. They reported no changes in their results given this knowledge.

Later they extended their keyset to 30 keys and noted the accuracy of given keys to the network, even expanding into the realm of utilising a separate keyboard. They found a given accuracy of 79% out of 300 ’test’ clicks.

They acknowledge that in the tests provided so far, the same user provided input onto the keys, such that they had trained a network in the users biometric attitude towards the keyboard. They found that given
a change in person and approach to impact pressure applied to each key that their neural network resulted in poor behaviour.

Their work expands into other touch-based input systems such as telephones, ATMs and more - however this escapes beyond the realm of our research. Finally they suggest a mechanism to counter this attack vector, using silent keyboards such as non-mechanical however they note the price and lack of
comfort these provide to users.

**Conclusion**

The most detailed aspect of this research is the 'touch-peak' of 2-3ms and training data, they utilise important methods that can be followed up on for my work. I plan to follow a similar pattern of testing two individual keys, then 5, then a range of keys. 

### 3.3 Keyboard Acoustic Emanations Revisited

[Paper](research/KeyboardAcousticEmanationsRevisited.pdf)

In 2009 Zhang, Feng and Tygar of the University of California produced a paper that expanded upon Asonov and Agrawals in the hope to address the inefficiency of their neural network. In their paper they report a success of identifying up to 96% accuracy when disregarding a new for training label data within a 10 minute period of sound recording. They announce the success of a 90% accuracy within 5 character random password identification with only the use of letters in fewer than 20 attempts by the adversary, leading to %80 accuracy within 75 attempts at 10 character random passwords.

They incorporate the use of the constraints applied by the English language and as such utilise a dictionary to help identify potentially invalid words and replace them with the most likely correct alternative.

They quickly address the previous flaws laid out by Asonov and Agrawals paper in which labelled training data is required for learning and given the same environmental variables are in play, variables in key impact
pressure lead to a severe failure within the previous paper.

The paper regards a superior technique over FFT for feature extraction and training of the neural network by utilising cepstrum features which details higher than FFT. Interestingly they admit that they are not aware whether the victim may be writing in English but instead address this by saying that given the accuracy of their results it would become apparent whether the user was writing in English or not given a few attacks.

They use clustering to help apply a class to each keystroke to a key but admit that it is potentially unreliable and as such much seed it randomly to avoid obvious overlap. A HMM (Hidden Markov Model) is used to correctly identify typical positioning of characters and likelihood of positioning given the English language, an example being ’h’ coming after ’t’ to form ’th’. Afterwards utilising a speller and grammar checking system to fill in any potentially unknown variables within words. Finally they apply this to a feedback trainer
which helps the classifier to identify potential random text at a later for password recognition. They only utilise words that had less than 1/4 of their components correct to help train the classifier and with this are able to identify the quality of the classifier; more feedback equals better quality as less mistakes have been made in the classification program.

**Conclusion**

The big push in this research is the use of Mel-cepstrum over FFT, although this technique is superior at analysis it is far more complex and could potentially be beyond my capabilities but is worth noting in detail. FFT is an easy technique to implement while Mel-cepstrum has been notably used in voice recognition software. They utilise clustering (see later on kmeans clustering) to classify keystrokes but describe this technique as 'standard clustering methods' (later research explains more detail kmeans clustering).

### 3.4 Cracking Passwords using keyboard acoustics and language modelling

[Paper](research/crackingpasswords.pdf)

One very substantial prior research piece is that of Andrew Kellys similar exploration into acoustic keylogging by building of the previous research of Asonov and Agrawal in 2004. The piece written in 2010 demonstrates extensive understanding of techniques provided by Asonov and Agrawal while expanding upon them to deliver a clear depth of expansive knowledge. Kelly provides an overview of different stages utilised in the
project with each stage isolating requirements for the project as a hole. Kelly explains the use of a ’press-peak’ for analysing the acoustic features from a keystroke which is compromised of two separate components a touch-peak and hit-peak; the touch-peak providing a further detailed analysis for digital
sound signalling.

![kae](research/images/kae.png)

Kelly explains the use of Asonovs and Agrawals neural networks for classifying keystrokes which resulted in a 79% success rate, this attack vector required labelled training data and suffered from variations in
accuracy with the pressure applied to each keystroke. Later Kelly mentions the expansion of this attack vector provided by Zhang, Zhou and Tygar in 2009, in which they utilised an unsupervised clusters of keystrokes - feeding these into unigram and bigram statistics to map clusters to the correct keys and later
applying a language model and dictionary for spell checking to then feed into a supervised classifier with the correct text. Kelly notes that Zhang, Zhou and Tygar found that utilising cepstrum feature extraction
over FFT (Fast Fourier Transform) yielded a much higher accuracy. By using a spell checker with a dictionary they were able to train their classifier and provide more accurate results when analysing keystrokes.

The paper explains that keystrokes often fall within the frequency range of 400-12000Hz, although Kelly does not explain whether the keyboards used are membrame or mechanical, in the case of our project - it’s a mechanical keyboard.

**Conclusion**

Overall I have provided a small subset of Kellys early analysis in his paper but the important details like in his use of feature extraction via FFT and Mel-cepstrum frequency analysis. The use of kmeans clustering over supervised learning is an interesting concept but I hope to implement both to verify these findings myself as machine learning is not a concept I am personally too familiar with.

## 4. Hardware

### 4.1 Smartphone Technology

In previous research in this field all microphone technology has been provided by professional recording equipment designed to be precise and offer accurate findings. In the case of my research we are using an off the shelf device that can be used by any user from any background with smartphones. Therefore my precision can potentially be poorer than previous research as the focus is on being as far from specific as possible. 

There are several operating systems used on smartphones ranging from Apples 'iOS' to Googles 'Android' and lesser popular operating systems such as Windows mobile and Linux hacked phones. 

While technology has pushed smartphones further than before and shall carry on doing so it's important the note that my findings are limited to this hardware and technology. Android is supported across multiple phones and API variations of the operating system with many different companies utilising and modifying it to give their users a precise design. As Android is supported and incorporated on more mobile devices than any other mobile operating system it seems the smart choice to try and reflect the worlds habits on smartphones. The phone in particular being used is the Samsung Galaxy S4, a flagship model from 2013. Old enough to no longer be prevalent with the S5, 6 & 7 models super seceding it but young enough to still be fully fleshed out and capable of handling our task. If the project works on this phone, it'll work on nearly all phones after it owing to legacy development.

![s4](hardware/s4.jpg)

​                                                                            (Samsung Galaxy S4)

At later stages I attempted to use a Samsung S6 Edge in place of the S4 but found that little changed in the results leading me to believe that the technology in the microphones was not overwhelmingly different.

![s6](J:\University\University\MSc\Project\Final\Corpus\hardware\s6.jpg)

​                                                                         (Samsung Galaxy S6 Edge)

#### Microphone

The important aspect of the phone itself is the Microphone with the focus of the hardware being on it's capabilities. Now unsurprisingly Samsung do not provide the specifications of the microphone that other manufactures will, normally we can expect a datasheet reflecting the quality of the microphone but in this case nothing is present. The model of phone is referred to the Samsung I9505 Galaxy S4 only provides minimal specifications on what the phone is capable of doing; such as wireless (WiFi) specifications.

Instead I opted to use a spectral frequency analyser and some code to identify the frequency spectrum that the S4 could sample at. We can assume that the phone samples human speech and that if humans can hear between a range of 20Hz-20KHz then the phone must be able to sample this correctly.

Assuming such that the highest range is 20KHz then we can use Nyquists theorem to determine that the highest safest sampling rate that will cause no audio loss is 2 times that, hence 40KHz, standard sampling rates around this value include 44.1KHz and 48KHz.

We can prove this further by demonstrating using a spectral analyser that the phone is able to identify frequency responses from upwards of 20KHz.

![spectro](hardware/spectro.png)

Therefore I knew that the phones microphone should be more than capable of identifying the keystrokes of the keyboard. However the accuracy may not be as high as more omnidirectional and precise microphones.

### 4.2 The Android Operating System

As mentioned prior this operating system designed by Google is found on more smartphones than any other operating system. Not all phones run the same versions with many running older versions rather than the newest versions. Vendors will often tailor Android for their users in the case of Samsung providing or closing certain features behind their security or providing enhanced features such as 'Samsung Pay'. 

![android](hardware/android.png)

​                                           (Image courtesy of [Wikipedia](https://en.wikipedia.org/wiki/Android_version_history))



* Samsung Galaxy S4 runs Lollipop (Android 5.0.1)
* Samsung Galaxy S6 Edge run Nougat (Android 7.0)

So by testing both these devices with the developed application we can sweep around 40% of all Android operating systems and in-between those too (between Android 5.x - 7.x).

#### Android Java

Android uses 'java' as it's primary programming interaction. Although it does not use the JVM (Java virtual machine) or bytecode like normal Java applications instead opting for it's own 'Dalvik' machine and bytecode. It provides the same interaction that Java does and is synonymously known as Java but it's not entirely the same working principle. Although for the purpose of this project, it won't make much difference in the long run.

### 4.3 Keyboard Hardware

In this project I have decided to utilise a mechanical keyboard over a typical membrane keyboard. Mechanical keyboards are louder and well structured internally compared to membrane and while this may seem like a trade off in terms of the attack vector - it's a controlled lab environment with a focus on pure identification and analysis to begin with.

The keyboard itself is the Razor Black Widow Ultimate 2014 Edition mechanical keyboard and while that name sounds intense it's a gaming keyboard with backlit elements and macro keys. It's designed to be powerful and loud which makes it ideal for analysis. 

![keyboard](/hardware/keyboard.jpg)

​                                                  (Razor Black Widow Ultimate 2014 Edition Keyboard)

Another keyboard is present but this one is a simple membrane keyboard and exists for purely for varying testing conditions.

## 5. Testing conditions

### 5.1 Constraints

The testing behind the project follows tight constraints in order to control the environment and tests as much as possible. Some elements are almost impossible to guarantee identical values for while others can be controlled fairly easily. Below are the list of constraints and variables that testing suffered from. 

For the **methodology** behind the testing see testing methodology, section 6. 

#### 5.1.1 Keyboard

As mentioned prior the keyboard used in this work was a Razor Black Widow Ultimate 2014 Edition Keyboard, a mechanical gaming keyboard with macro keys. Designed for multi-purpose scenarios. 

###### 5.1.1.1 Location

The location of the keyboard is as relevant as the location of the phone, both need to remain identical throughout all testing and cannot be subject to change else the values and training data provided to the application will be invalid. By keeping the keyboard in the same location each time in proportion to the phone we guarantee that our testing will not be impacted by variations in distance. 

Using a laser cut frame from wood I was able to fix the location of the keyboard at all times as with the location of the smartphone. For more information on the wooden frame see section **5.1.3**.

![frame_keyboard](/testing_conditions/frame_keyboard.JPG)

###### 5.1.1.2 Membrane vs Mechanical

I choose the black widow keyboard owing to it's mechanical nature and prominent feature set. There are multiple mechanical keyboards on the market but for me this keyboard was distinct and easily available being my personal keyboard of choice. Although prior research had investigated the differences they too felt that mechanical keyboards were a step in the right direction. The important detail for acoustic keylogging is that mechanical keyboards are often much louder, although this can vary based on the switches used - in the case of the Razor model used it's a custom bespoke switching system.

For distinct differences in membrane versus mechanical see the diagram below.

![mechvsmem](/testing_conditions/mechvsmem.png)

​                                        (Mechanical left, Membrane right. Image from [prohavit.com](https://www.prohavit.com/blog/membrane-keyboard-vs-mechanical-keyboard/))

As can be seen, mechanical hits the backplate fierce and hard whereas membrane is a soft flexible impact and may vary on the noise given.

##### 5.1.2 Smartphone

As mentioned prior the smartphone used was the Samsung Galaxy S4 primarily with second-hand testing on an S6 Edge. 

###### 5.1.2.1 Operating System

Albeit the operating system used in this case fairly universal and as such is not so much a constraint as a benefit. However it must be said that the operating system used was Android and not another, even then versions 5.0.1 (Lollipop) and 7.0 (Nougat).

###### 5.1.2.2 Microphone

The placement and positioning on the phone(s) is important for microphone usage in this project. For example while the S6 Edge and S4 may look very similar their microphone placements are different. Firstly both phones have dual microphones and offer one on the top and bottom faces of the device, however the S4 and S6 mirror each other with placement such that the S4s bottom microphone is on the left hand portion of the face while the S6s microphone is on the right hand side. As mentioned in the hardware section that the technology of the microphone can vary on the how well data can be sampled, this is a constant provided by the phone model itself but later models may use more sophisticated microphone technology.

When testing I had to be cautious with the wooden frame not to obstruct the microphones.

![frame_phone](testing_conditions/frame_phone.JPG)

* Samsung S4 sitting in frame, notice slots next to the bottom and/or top of the device to provide space                  for the microphones.
* The phone can be positioned in 8 different locations for testing purposes.               

##### 5.1.3 Lab conditions

The area in which I recorded all of my samples and results. Initially I recorded some samples in Canterbury and then when I moved back home for the final months of my MSc I recorded the remaining samples there. I live very close to Gatwick airport on a remote farm under the flight path so one of my main considerations was avoiding noise pollution from outbound and inbound aircraft. 

The lab itself was my living room as this was the most isolated and quietest part of my house and I recorded on top of a metal plate to avoid creaking of a wooden table. 

I created a wooden frame to fix the locations of the smartphone and the keyboard as seen in previous images of this section. The frame itself was designed in the shed to match the measurements of the Samsung S4 as well as the Razor keyboard. It was intended to provide modularity in the fixed position by allowing up to 8 different positions for the smartphone to be fixed in; all centring around the keyboard. While providing space for both microphones on the phone. 

![frame_empty](testing_conditions/frame_empty.JPG)

​                                              The frame with neither keyboard or smartphone present.

### 5.2 Variables

Throughout the testing their are variables that exceed my control, these variables may influence the outcome of the results of testing and are mentioned below.

#### 5.2.1 Background noise

As mentioned I live next to Gatwick and even before then I lived with 5 other students. Background noise from aircraft, farm animals, people, floorboards creaking etc are all likely to disturb the accuracy of the tests. I attempted to minimize the effects of this by only recording at dormant times (Where little people are around) and in-between aircrafts landing and taking off. You can see in my testing recordings that I actually pause before proceeding to training more data as to avoid specifically aircraft interference. 

#### 5.2.2 Phone model

While the phone model in my project is fixed it's important to note that this is a variable in the real world and may not reflect all potential outcomes of the real world under similar testing procedures. I did utilise 2 different makes of Samsung smartphones to try and demonstrate this but other manufactures or entirely different phones in general may be impacted by these testing conditions.

#### 5.2.3 Location of phone

The phone can change it's location as mentioned prior about the frame although this variable is more of a constant set where there are only 8 potential locations for the phone to be, however depending on the location it is more than likely to change the values associated with the results.

#### 5.2.4 Keyboard

While in the constants of this testing I will be using the Razor mechanical keyboard, in the real world the keyboard being monitored may be of varying size or style. It's important to note that this sampling keylogger will only be trained to this specific keyboard and holds no promises on it's capability of identifying keys from other keyboards.

#### 5.2.5 Impact strength & location

When you press a key on a keyboard you may vary the strength and location of your finger as it makes contact with the key. This is important as location is mostly fixed thanks to the wooden frame but given the impact zone may infer different values based on the location of the impact. For example, when we look at the letters 'Q' and 'W' they are situated next to one another, a slight impact to the top-left corner of 'W' may sound like a 'Q'. 

The impact strength itself will be controlled as best as plausible in the testing environment, in the real world this strength may vary based on user, keyboard, attitude and much more. 















