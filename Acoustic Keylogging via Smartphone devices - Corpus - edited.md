<style>
	.highlight{
		background-color: yellow;
	}
</style>

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
   * ​

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

<span class="highlight"> Almost every human in the First World owns a smartphone. These modern day devices often contain technology more powerful and sophisticated than the rockets that delivered man to the moon. </span>

Considering this, the potential power behind the average smartphone is huge, even for the purpose of breaking security measures. Computer keyboards are not a new invention and have been rooted to the development of computers since their creation; however they are fundamentally at the hand of every and all sensitive data entry. Sensitive data could reflect bank details, passwords, personal or confidential information and more. 

The dissertation that this corpus supports aims to challenge whether a modern day smartphone can acoustically eavesdrop on a keyboard through side-channels in the <span class="highlight">sound</span> produced by pressing the keys on the board.

#### 1.2.2 Aim

This corpus aims to provide and support the dissertation associated with it such that any <span class="highlight">reference of relation to the material, results or development of the dissertations logic, applicants or findings can be backed up and catalogued.</span> This corpus will <span class="highlight">briefly</span> cover certain aspects of the project and the details can be found in the <span class="highlight">body</span> of the dissertation. Instead this corpus aims to provide a uniformed catalogue of data used as referencing points in the dissertation thesis itself. <span class="highlight"> last 2 sentences seem to be repeating each other? </span>

### 1.3 Special Thanks

This project could not have been completed without the following people and groups who have provided wonderful guidance and support throughout the project.

<span class="highlight">I have captialised their titles </span>

* Budi Arief - Supervisor, <span class="highlight">Computer Security Lecturer.</span>
  * Met with me regularly to conduct guidance meetings and help keep me on track of the topic at hand, always firm and willing to provide assistance when needed.
  * Founded the project concept and passed it onto me.
* Samuel Williams - PhD candidate, Programming Language Implementation specialist.
  * Provided fantastic knowledge on artificial intelligence and had a deep appreciation for the research topic covered in this material.
* Alice Mo - Data Mining Analyst and MSc Candidate at University College London
  * <span class="highlight">Fundamentally showed and helped deal with resolving data to identify useful traits and patterns. </span>
* Michael Berry - PhD, Software Engineer, Electronics Tinkerer and Radio Licence Holder.
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
* 14/8/2017 (On Skype) - [View](https://youtu.be/rXuJJ0NG7Ys)

In-between June and August I lost two of my recordings. 

### 2.3 Meeting summaries

##### 31/1/2017 - Initial Preparation

Discussed hardware capabilities, such as whether the phone being used has multiple microphones, where they are and what sort of sensors to utilise.

Discussed controlled environment settings:

- Specific keyboard to use, in this case mechanical keyboard model "Razer BlackWidow 2014 Ultimate" - using <span class="highlight">Razer's</span> patterned mechanical keys.
- Specific to Android OS only for the purpose of the research
- 20 presses of specific keys, 'Q', 'W', etc.
- Lasercut potential frame to hold keyboard and phone, ensure that the distance between them is always fixed and therefore stops variations in this.
- <span class="highlight">Decided to use my Android phone to undertake this project.</span>
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

Initially this was a demoralising iteration, I found that the accelerometer was slow within the Android SDK and that I would not <span class="highlight">reliably</span> be able to identify or determine key presses given such little ranging values over a sample, such that I decided for the time being to focus solely on acoustic keylogging rather <span class="highlight">than<span> other features. 

Decided to go back to the 'drawing' board and look at research more thoroughly, other assessments had gotten in my way and little work had been made through this iteration.

Had difficulties isolating the memory storage on the Smartphone as it appeared under a 'virtual' filesystem such that I couldn't accurately locate the file that I was saving all my samples and readings to.

Found that amplitude wasn't a good measurement for feature extraction alone and that frequency would be an absolute requirement.

Had laser cut a frame however to hold the phone and keyboard in place.

##### March, April, May

A lot of this time was spent working on assessments, exams and job interviews. Evaluation of research was the focus in this period while the development occurred post June. As such I shall present the researched papers and a link to my evaluations of those. These papers provided the foundation of the majority of my work, with research from Andrew Kelly featuring prominently.

* Cracking Passwords using keyboard Acoustics and Language Modeling - Andrew Kelly (2010)
* Keyboard Acoustic Emanations - Asonov and Agrawal (2004)
* Keyboard Acoustic Emanations Revisited - Zhang, Feng, Tygar (2009)
* Electronic emanations of wired and wireless keyboards - Vuagnoux and Pasini (2009)

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

Unfortunately I lost the recording for this meeting but I did however make some notes on the topics mentioned. The focus of the meeting was applying a Fourier transform across a discrete dataset of values for analysis in the frequency domain. Such that we could later pass this into a feature extraction function that would return us distinct features of keypresses.

##### 12/07/2017 - Implementation progress update

Another lost audio recording for this meeting.

I had successfully written a feature extraction algorithm that was able to identify distinct differences in frequency and magnitude between two key presses, albeit there were complications with live audio recording as to be expected.

The next focus on was on refining this feature extraction if possible and looking into a primitive machine learning algorithm to help classify and train the keys being pressed. In this case the <span class="highlight">focus was on</span> a supervised algorithm.

##### 21/7/2017 

[Audio](meetings_audio/21.07.m4a)

A setback  occurred where my AudioRecord API ceased to operate and instead started spurring errors, after fixing these owing to updated Android API permission system the project was back on track.

Discussed the possibility of focussing on multiple keyboards but for the time being decided to look at just one keyboard until later period. Talked about storing the data and dealing with Androids file system in a manner that can be adjusted accordingly if need be. Java offers serialisation, a useful mechanism of preserving the data encapsulated within an object at runtime; potential for this tool to be used. Preserving data comes in the form of being able to then use this as a measurement of comparison for later, i.e I'm able to identify the key C because I have told my program from training that key C sounds like this.

Decided that the phone should handle everything, previously there was a thought of potentially having a machine elsewhere decode the live audio into information but instead the confirmation of the phone being the sole processing machine was decided. Rationality for this was user ability, if anyone owns a phone then they also can do what this project aims for.

Discussed potentially having a visual display of characters being decoded as an end goal, however for this to be effective it would require that the device was able to quickly identify as many keys as possible as well as having a high degree of accuracy in doing so.

Talked breifly about Mel-cepstrum Frequency Analysis, a technique often used in voice recognition systems although this methodology was too foreign to be adopted. 

Finished up with discussing the corpus and dissertation display and layout, decided to use markdown and provide the corpus in a HTML relative structure.

##### 14/8/2017 (On Skype) 

[Audio](https://youtu.be/rXuJJ0NG7Ys) - Provided on YouTube, otherwise it's 1.4GB.

**Note** - The previous 3 weeks consisted of back and forth between me and Budi, trying to arrange a meeting as both of us were unavailable at several periods. 

This meeting was a final conclusive meeting of the project coming to an end. I spent time explaining the working system for the keylogger as well as providing details on several anecdotes regarding the system. Details included:

* Feature extraction
* Mean average supervised learning
* <span class="highlight">K-means</span> unsupervised learning
* Saving results
* Identifying keystrokes based on results

<span class="highlight">The results </span>of <span class="highlight">k-means</span> clustering were more accurate than mean average<span class="highlight">. K-means</span> scored around ~60% while mean average scored around ~52%. At this point the focus was on writing the corpus and working towards the dissertation. 

**Note** - A final meeting is planned for the 29/8/2017 but since the Corpus will have been submitted it will not be documented, this meeting aims to provide details and feedback on the state of the dissertation.

---

## 3. Research

### 3.1 Accelerometer Side Channel Attacks

[Paper](research/AccelerometerSideChannel.pdf)

Using the accelerometer on Android based smartphones to determine a users phone pin/pattern unlocking code. Research in this field shows that success rates in controlled environments are high (such as the user sitting down being motionless) whereas in uncontrolled environments rates dropped but still maintained a concerning high level of accuracy.

<span class="highlight">They provided relevant research from others in the field in similar veins of collecting data, previous papers referenced in this include: doesnt make grammatical sense!!</span>

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

###3.2  





