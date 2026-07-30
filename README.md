# SIL Translation Test



### Description
This repository is for documentation of Scripture App Builder, Reading App Builder, Keyboard App Builder, and Dictionary App Builder. It aims to keep a version history of all documents and translate them into several languages via Crowdin translation. This repository will also automatically convert, format, and output documentation as the user needs.



# Setup

### Description

#### GitHub
The GitHub workflows are scripts that perform tasks automatically. This repository has only one workflow named “auto translate.” In this case, the workflow formats files, translates documents, and outputs PDFs. The workflow starts whenever a file is submitted or changed in the repository, or it can be manually started.

#### Crowdin
Crowdin is a business that provides translation software for its users. Crowdin has also created a GitHub workflow integration that allows GitHub workflows to send and receive files from Crowdin projects. This integration syncs this GitHub repository with its Crowdin project, allowing translations to be created and downloaded into a branch named "translations."

#### Tokens
In order for the GitHub workflow and Crowdin to work together, they use tokens to identify each other. Tokens are a unique series of numbers (and sometimes letters) that must be copied and entered into the GitHub repository as an environment secret. There are three tokens that need to be generated and collected for the GitHub workflow to properly run: `CROWDIN_PROJECT_ID`, `CROWDIN_GITHUB_TOKEN`, and `CROWDIN_PERSONAL_TOKEN` (please remember these names). The user will have to add all these tokens to their proper locations in the GitHub repository. Instructions on how to do so are listed in the "configuring tokens" section below.

#

Here are examples of what the tokens will look like and their needed names. **THESE ARE EXAMPLES AND NOT VALID**

`CROWDIN_PROJECT_ID` ≈ 346867

`CROWDIN_GITHUB_TOKEN` ≈ ghp_i7KCtEo9rUxgDZZ6k9xY4YydWZcBsP2EJUbd

`CROWDIN_PERSONAL_TOKEN` ≈ 9fcd75f1e2fa8132788171db0ca12624c65e0855d5af9391410e5402c4a7d479a39429b2d2217509



#
### Configuring tokens

#### PLEASE NOTE: Some tokens can only be viewed once before becoming hidden from you. Make sure you temporarily copy them someplace safe like a notepad app before exiting the webpage. There are three tokens that need to be entered as GitHub secrets. Instructions on how to find and add the tokens are shown below.

#### CROWDIN_PERSONAL_TOKEN
1. To create the `CROWDIN_PERSONAL_TOKEN`, open the Crowdin project webpage. (this can be found on the left menu bar at the bottom), click on the user's Crowdin profile picture, and select "settings". This will open the Crowdin user's settings page.

![Description](README_pics/Screenshot_20260710_145305.png)

2. Then find the "API" tab and click on it.

![Description](README_pics/Screenshot_20260710_145646.png)

3. Then select "New Token" under "Personal Access Tokens," and a screen will appear asking for a token name and permissions.

<img src="README_pics/Screenshot_20260723_104701.png" width="400" height="800" />

4. Select "All Scopes" and enter a name for the token (This name can be anything you choose). Then select the "Create" button in the bottom-right corner.

<img src="README_pics/Screenshot_20260723_105535.png" width="400" height="800" />

5. After that, Crowdin may prompt you for your account password. Fill it in and hit confirm.

<img src="README_pics/Screenshot_20260723_105754.png" width="700" height="1400" />

6. Then a token will be generated in a textbox in the middle of the screen. Click the copy button on the right side of the textbox and temporarily paste it someplace safe.

<img src="README_pics/Screenshot_20260723_105833_blackedout.png" width="700" height="1400" />

7. Finally, now that the token has been generated and saved, it needs to be added to the GitHub repository secrets. Instructions can be found in the "Adding tokens to GitHub secrets" section.


#

#### CROWDIN_PROJECT_ID
1. To find the `CROWDIN_PROJECT_ID`, open the Crowdin project webpage and open the project. On the right-hand side, under the "dashboard" tab, it will be listed. Click it to copy the token and save it.

![Description](README_pics/Screenshot_20260710_153219.png)

2. Now that the token has been saved, it needs to be added to the GitHub repository secrets. Instructions can be found in the "Adding tokens to GitHub secrets" section.


#

#### CROWDIN_GITHUB_TOKEN
1. To generate the `CROWDIN_GITHUB_TOKEN`, open the GitHub webpage, click on the user's GitHub profile picture, and select "settings". This will open the GitHub user's settings page.

![Description](README_pics/Screenshot_20260710_154215.png)

2. Then scroll down to find the "Developer Settings" tab at the bottom left and click on it.

![Description](README_pics/Screenshot_20260710_154247.png)

3. Then select "Tokens (classic)" under "Personal Access Tokens" and select "Generate new token (classic)".

![Description](README_pics/Screenshot_20260710_154629.png)

4. Enter the "GITHUB_TOKEN" into the note field and set the Expiration option to "No Expiration". Then select the repo, workflow, and write:packages boxes. Afterward, scroll to the bottom of the webpage and select the green "Generate token" button.

<img src="README_pics/Screenshot_20260727_121126.png" width="800" height="1200" />

5. Click the blue copy button next to the token and paste the token in a notepad app.

<img src="README_pics/Screenshot_20260727_122808_blackedout.png" width="800" height="1200" />

6. Finally, now that the token has been generated and saved, it needs to be added to the GitHub repository secrets. Instructions can be found in the "Adding tokens to GitHub secrets" section.



### Adding tokens to GitHub secrets
First, you must be an administrator of the GitHub repository. If you are not, you need to contact one. You can tell if you are an administrator if you scroll to the top of the GitHub webpage: there will be a tab labeled "settings." Please note this is a different GitHub settings tab than the one mentioned previously, as this tab is for the GitHub repository settings while the previous one was for GitHub account settings.

<img src="README_pics/Screenshot_20260713_125818.png" width="600" height="1000" />

If there is a settings tab, select it, then find the "Secrets and variables" button on the left bar and select "Actions" in the drop-down menu. Then click "New repository secret."

<img src="README_pics/Screenshot_20260713_125904.png" width="800" height="1200" />

Fill in the "name" and "secret" information and click "Add secret". Make sure you only name the tokens what they are called in this document (`CROWDIN_PROJECT_ID`, `CROWDIN_GITHUB_TOKEN`, `CROWDIN_PERSONAL_TOKEN`). If this is not done, then the GitHub workflow will not register the tokens and Crowdin will not work.

<img src="README_pics/Screenshot_20260723_141526.png" width="800" height="1200" />

In addition, the `CROWDIN_PROJECT_ID` must be manually entered into the `project_id: "XXXXXX"` field in the "crowdin.yaml" file, which is located inside the repository.

<img src="README_pics/Screenshot_20260723_143804.png" width="800" height="1200" />


#
### Configuring Crowdin
To properly use Crowdin with this GitHub workflow, it is necessary to tweak certain features of the software to get the best results.


#### Duplicate Strings
A setting that needs to be enabled is "Duplicate Strings." It allows two identical sentences to only be counted as one. This reduces the total word count and therefore costs.

To enable this, you need to go into the "settings" tab at the very right.

<img src="README_pics/Screenshot_20260720_140218.png" width="400" height="800" />

Then scroll down to the "import" bar and select it.

<img src="README_pics/Screenshot_20260720_140247.png" width="300" height="600" />

After that, look to the right to find the "Duplicate Strings" menu and select the "Hide (strict detection)" option.

<img src="README_pics/Screenshot_20260720_140338.png" width="1000" height="2000" />

Next, select "Skip tags" under "Word and character count". This setting also reduces the word count by not allowing data tags to be marked as words.



# How to Use

### Editing Documents

The main process of editing documents hasn't changed, however there are some key differences and steps that have to be followed to work with this repository.

The first difference is with the document editor. While most documents are edited with Microsoft Word this repository uses Libreoffice. Libreoffice is a free and opensource document editor which provides an identical experience to Microsoft Word. This change was made in an attempt to move away from paid software. Because of this change the file formats documents are in has changed as well, no longer using the .doc or .docx but instead .fodt format. Changing this doesn't affect how the document is used only which file type the user must select when saving the document.

The second difference is how images are inserted into the documents. Images are inserted as image links not fully images, this means that while the image is displayed in the document it is just referencing a separate image file located outside of the document. Because of this difference the method of adding an image slightly changed, images are still inserted by clicking the "Insert" tab and selecting the "Image" option, however the "Link" checkbox must also be checked before adding the desired image.

###### Documents
All documents need to be submitted in English, as Crowdin will handle all translations to non-English languages. All documents should be in .fodt format and should only be added (or modified) in `docs-en/fodt/(app builder name)/(file)`, for example, `"docs-en/fodt/SAB/Scripture-App-Builder-01-Installation-Instructions.fodt".`

###### Images
In this repository, images are handled differently than most other documentation repositories. Images are not inserted into the documents themselves, but instead are inserted as links pointing to separate image files. This means that every document has a folder next to it that contains all the images displayed in that document. For example, "Scripture-App-Builder-01-Installation-Instructions.fodt" would be next to a folder named SAB01. This folder would have all the images the document would use. More examples of this would be "Dictionary-App-Builder-04-Distributing-Apps.fodt" next to DAB04, and "Reading-App-Builder-07-Using-aeneas-for-Audio-Text-Synchronization.fodt" next to RAB07.

<img src="README_pics/Screenshot_20260715_151502.png" width="300" height="600" />
<img src="README_pics/Screenshot_20260722_161042.png" width="300" height="600" />
<img src="README_pics/Screenshot_20260722_161127.png" width="300" height="600" />

The reason why this repository uses this system is that it makes it incredibly easy to switch out images in a document. Since screenshots containing English text cannot be translated by Crowdin, the next best solution is to replace these screenshots with ones containing text in the correct language. The GitHub workflow will automatically replace the screenshots; however, the user still needs to manually supply all screenshots. The images are located in images/(language)/(app builder name)/(image folder), for instance, "images/en-US/KAB/KAB02", and do not need to conform to a specific file format. Simply drop the images into the correct folder, and the workflow will handle the rest.


### Submitting Documents
All submissions should be put into the "main" branch of the GitHub repository, and should be added into the following locations based on their types. Instructions on how to add files to the repository are shown below.

All English documents should be submitted into the `docs-en/fodt/` folder and should not be submitted anywhere else in the repository. Example `docs-en/fodt/RAB/example_filename.fodt` or `docs-en/fodt/DAB/example_filename.fodt`

All images will be put into the `images/` folder and should not be submitted anywhere else in the repository. Example `images/fr-FR/KAB/KAB02/example_filename.png` or `images/en-US/SAB/SAB07/example_filename.png`

1. Click on the "docs-en" folder on the GitHub project webpage. After that click on "fodt" and then the specific app builder the documents are for (SAB RAB KAB DAB).

<img src="README_pics/Screenshot_20260730_094837_arrow.png" width="700" height="1400" />

2. On the top right side of the webpage there will be a button that says "Add file" click on it and select the "Upload files" button from the drop down menu

<img src="README_pics/Screenshot_20260730_103716.png" width="500" height="1000" />

3. Click on the "Choose your files" button in the center of the screen and pick the files you want to upload to the folder. Then after that is done click the green "Commit changes" button at the bottom of the screen.

<img src="README_pics/Screenshot_20260730_100307.png" width="700" height="1400" />


#
Below is a diagram of the repository file structure with notes on what each folder does.
```
Repository Overview
│
├── docs   <---------- DO NOT SUBMIT DOCUMENTS IN THIS FOLDER OR ANYTHING IN IT. This is where Crowdin puts the translated documents so any documents submitted here will be overwritten with the Crowdin documents.
│   │
│   ├── de-DE
│   │   ├── fodt
│   │   ├── odt
│   │   └── pdf
│   │
│   ├── es-ES
│   │   ├── fodt
│   │   ├── odt
│   │   └── pdf
│   │
│   └── fr-FR
│       ├── fodt
│       ├── odt
│       └── pdf
│
├── docs-en 
│   │
│   ├── fodt   <----------- SUBMIT DOCUMENTS HERE. This is where the English documents should be submitted.
│   │   ├── DAB
│   │   ├── KAB
│   │   ├── RAB
│   │   └── SAB
│   │
│   ├── odt
│   │   ├── DAB
│   │   ├── KAB
│   │   ├── RAB
│   │   └── SAB
│   │
│   └── pdf
│       ├── DAB
│       ├── KAB
│       ├── RAB
│       └── SAB
│
└── images   <----------- SUBMIT IMAGES HERE. This is where the image files should be submitted. Make sure you separate the images based on language.
    ├── de-DE
    │   ├── DAB
    │   ├── KAB
    │   ├── RAB
    │   └── SAB
    ├── en-US
    │   ├── DAB
    │   ├── KAB
    │   ├── RAB
    │   └── SAB
    ├── es-ES
    │   ├── DAB
    │   ├── KAB
    │   ├── RAB
    │   └── SAB
    └── fr-FR
        ├── DAB    
        ├── KAB
        ├── RAB
        └── SAB
```



### Workflow

1. Scroll to the top of the webpage and click on the actions tab at the top of the screen. Then click on the "auto translate" button under the green button labeled "new workflow".

<img src="README_pics/Screenshot_20260723_112417.png" width="700" height="1000" />

2. Find the "Run workflow" button on the right side of the screen and select the drop-down menu. Click the "Run workflow" option.

<img src="README_pics/Screenshot_20260713_155959.png" width="700" height="1000" />

3. The workflow is now running in the background. You can click the "Convert" button to view the output of the workflow. Or, when the workflow has finished, click "Summary" to view the artifact outputs.

<img src="README_pics/Screenshot_20260713_160239.png" width="700" height="1000" />



# Outputs
The workflow will produce two types of outputs. First, it will generate all the translated files and add them to the "translations" branch. The user has the option to merge the translations branch into the main branch if they want the new documents to be easily accessible.

The second output is a .zip artifact composed of PDFs from both English and non-English languages. This can be found by going to the workflow and clicking the "Summary" button.



# Conclusion
I promise you I will finish this one day.
