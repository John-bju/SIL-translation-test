# SIL Translation Test

### Description
This repo is for documentation of SAB, RAB, DAB, KAB which aims to keep a version history of all documents and translate them into several languages via crowdin translation. This repo will also automatically convert, format, and output documentation as the user needs.



# How to Use
### Submitting
All submissions should be put into the "main" branch of the github repository, and should be added into the following locations based on the following types. 

###### Documents
All documents need to be submitted in english, as crowdin will handle all translations to non-english languages. All documents should be in .fodt format and should only be added (or modified) in `docs-en/fodt/(app builder name)/(file)` for example `"docs-en/fodt/SAB/Scripture-App-Builder-01-Installation-Instructions.fodt".`

###### Images
In this repo images are handled differently than most other documentation repos. Images are not inserted into the documents themselves, but instead are inserted as links pointing to separate image files. This means that every document has a folder next to it that contains all the images displayed in that document. For example "Scripture-App-Builder-01-Installation-Instructions.fodt" would be next to a folder next to it named SAB01, this folder would have all the images the document would use. More examples of this would be "Dictionary-App-Builder-04-Distributing-Apps.fodt" DAB04, Reading-App-Builder-07-Using-aeneas-for-Audio-Text-Synchronization.fodt RAB07.

<img src="README_pics/Screenshot_20260715_151502.png" width="400" height="800" />

The benefit and reason why this repo uses this system is that it makes it incredibly easy to switch out images in a document. Since screenshots containing english text can not be translated by crowdin the next best solution is to replace these screenshots with ones containing text in the correct language. The github workflow will automatically replace the screenshots, however the user still needs to manually supply all screenshots. The images are located in images/(language)/(app builder name)/(image folder) for instance "images/en-EN/KAB/KAB02" and do not need to conform to a specific file format. Simply drop the images into the correct folder and the workflow will handle the rest.

#
### Workflow

The github workflow is a script that performs tasks automatically. In this case it formats files, translates documents, and outputs pdfs. The workflow starts whenever a file is submitted or changed in the repo, or it can be started by following the steps below.


Navigate to the actions tab at the top of the screen.

<img src="README_pics/Screenshot_20260713_155930.png" width="700" height="1000" />

Find the "run workflow" button on the right side of the screen and select the dropdown menu. Click the "Run workflow" option.

<img src="README_pics/Screenshot_20260713_155959.png" width="700" height="1000" />

The workflow is now running in the background. You can click the "Convert" button to view the output of the workflow. Or when the workflow has finished click "Summary" to view the artifact outputs.

<img src="README_pics/Screenshot_20260713_160239.png" width="700" height="1000" />



#
### Crowdin Sync
Crowdin is a business that provides translation software for its users. Crowdin has also created a github workflow intergration that allows github workflows to send and receive files from Crowdin projects. This integration syncs this GitHub repo with its Crowdin project, allowing translations to be created and downloaded into a branch named "translations."


###### Tokens
In order to set up the github integration the user must enter the correct tokens into the github project. Tokens are a unique series of numbers that allow the github project and the Crowdin project to identify themselves and intergrate properly. The steps to find and enter all tokens are listed below. 

There are three tokens that need to be entered into the github secrets tab in the settings of the repo.

`CROWDIN_PERSONAL_TOKEN:` To create this click on the user's Crowdin profile picture and select "settings".

![Description](README_pics/Screenshot_20260710_145305.png)

Then find the "API" tab and click on it

![Description](README_pics/Screenshot_20260710_153219.png)

Then select "New Token" under "Personal Access Tokens" and a token will be generated.


`CROWDIN_PROJECT_ID:` To find this go to the crowdin project webpage and on the right hand side under the "dashboard" tab, there it will be listed.

![Description](README_pics/Screenshot_20260710_154215.png)

`CROWDIN_GITHUB_TOKEN:` To generate this click on the user's github profile picture and selecting "settings".

![Description](README_pics/Screenshot_20260710_154247.png)

Then scroll down to find the "Developer Settings" tab and click on it.

![Description](README_pics/Screenshot_20260710_154629.png)

Then select "Tokens (classic)" under "Personal Access Tokens" and select "Generate new token (classic)".


###### How to add tokens to the repo.
First you must be an administrator to the github repo, if you are not then you need to contact one. Next navigate over to the settings tab at the top and select it, then find the "Secrets and variables" button and select "Actions". Then add each token as a secret with a name given in this document.


<img src="README_pics/Screenshot_20260713_125818.png" width="600" height="1000" />

<img src="README_pics/Screenshot_20260713_125904.png" width="800" height="1200" />

In addition, the `CROWDIN_PROJECT_ID` must be manually entered into the `project_id: "XXXXXX"` field in the "crowdin.yaml" file, which is located inside the repo.

#
### Outputs
The workflow will produce two types of outputs. First it will generate all the translated files and add them to the "translations" branch. The user has the option to merge the translations branch into the main branch, if they want the new documents to be easily accessible.

The Second output is a .zip artifact composed of pdfs from both english and non-english languages, this can be found by going to the workflow and clicking the "Summary" button.



# Crowdin Settings
To properly use Crowdin with this github workflow it is necessary to tweak certain features of the software to get the best results.

#
### Duplicate Strings
A setting that needs to be enabled is "Duplicate Strings", it allows two identical sentences to only be counted as one. This reduces the total word count and therfore costs. 

To enable this you need to go into the "settings" tab at the very right.

<img src="README_pics/Screenshot_20260720_140218.png" width="400" height="800" />

Then scroll down to the "import" bar and select it.

<img src="README_pics/Screenshot_20260720_140247.png" width="300" height="600" />

After that look to the right to find the "duplicate strings" menu select the "Hide (strict detection)" option.

<img src="README_pics/Screenshot_20260720_140338.png" width="1000" height="2000" />

Next select "Skip tags" under "Word and character count". This also reduces the word count by not counting tags used for data as words.

<img src="README_pics/Screenshot_20260720_140405.png" width="500" height="1000" />
