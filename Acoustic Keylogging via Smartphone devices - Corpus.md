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

   * Keystroke Dynamics
   * Audio Feature Extraction
   * Keyboard Acoustics
   * Audio Visual Extraction
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

Every fortnight I met my supervisor Budi Arief to discuss the project undertaken. These meetings were intended to provide insight into the current status of the project while assisting in any issues and providing other forms of support to the project.

### 2.2 Audio recordings

Not all meetings were recorded but for nearly all of them I have provided a recording if they are wanted. 

