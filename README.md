setup

  accounts
  tokens
  crowdin
  
how to use

  submitting
  workflow runnning
  outputs


# SIL Translation Test

### Description
This repository is for documentation of Scripture App Builder, Reading App Builder, Keyboard App Builder, and Dictionary App Builder which aims to keep a version history of all documents and translate them into several languages via Crowdin translation. This repository will also automatically convert, format, and output documentation as the user needs.



# Setup

### Description

#### Github
The Github workflows are scripts that performs tasks automatically, this repository has only one workflow named “auto translate.” In this case the workflow formats files, translates documents, and outputs PDFs. The workflow starts whenever a file is submitted or changed in the repository, or it can be manually started.

#### Crowdin
Crowdin is a business that provides translation software for its users. Crowdin has also created a Github workflow integration that allows Github workflows to send and receive files from Crowdin projects. This integration syncs this GitHub repository with its Crowdin project, allowing translations to be created and downloaded into a branch named "translations."

#### Tokens
In order for the Github workflow and Crowdin to work together they use tokens to identify eachother. Tokens are a unique series of numbers (and sometimes letters) that must be copied and entered into the Github repository as a enviroment secret.



### Configuring tokens

#### PLEASE NOTE: Some tokens can only be viewed once before becoming hidden from you. Make sure you temporarily copy them someplace safe before exiting the webpage. There are three tokens that need to be entered into as Github secrets. Instructions on how to add the tokens are shown below.

#

`CROWDIN_PERSONAL_TOKEN:`
1. To create this open the Crowdin project webpage and click on the user's Crowdin profile picture and select "settings".

![Description](README_pics/Screenshot_20260710_145305.png)

2. Then find the "API" tab and click on it

![Description](README_pics/Screenshot_20260710_153219.png)

3. Then select "New Token" under "Personal Access Tokens" and a screen will appear asking for a token name and permissions.

<img src="README_pics/Screenshot_20260723_104701.png" width="600" height="1000" />

4. Select "All Scopes" and enter a name for the token (This name can be anything you choose). Then select the "create" button in the bottom right corner.

<img src="README_pics/Screenshot_20260723_105535.png" width="600" height="1000" />

5. After that Crowdin may prompt you for your account password, fill it in and hit confirm.  

<img src="README_pics/Screenshot_20260723_105754.png" width="600" height="1000" />


#

`CROWDIN_PROJECT_ID:`
1. To find this open the Crowdin project webpage and on the right hand side under the "dashboard" tab, there it will be listed.

![Description](README_pics/Screenshot_20260710_154215.png)

#

`CROWDIN_GITHUB_TOKEN:`
1. To generate this open the Github webpage and click on the user's Github profile picture and select "settings".

![Description](README_pics/Screenshot_20260710_154247.png)

2. Then scroll down to find the "Developer Settings" tab and click on it.

![Description](README_pics/Screenshot_20260710_154629.png)

3. Then select "Tokens (classic)" under "Personal Access Tokens" and select "Generate new token (classic)".

#
### How to add tokens as Github secrets.
First you must be an administrator to the Github repository, if you are not then you need to contact one. You can tell if you are an administrator if you scroll to the top of the webpage there will be a tab labled "settings." Select it and then find the "Secrets and variables" button and select "Actions". Then add each token as a secret with a name given in this document.


<img src="README_pics/Screenshot_20260713_125818.png" width="600" height="1000" />

<img src="README_pics/Screenshot_20260713_125904.png" width="800" height="1200" />

In addition, the `CROWDIN_PROJECT_ID` must be manually entered into the `project_id: "XXXXXX"` field in the "crowdin.yaml" file, which is located inside the repository.



### Configuring Crowdin
To properly use Crowdin with this Github workflow it is necessary to tweak certain features of the software to get the best results.

#### Duplicate Strings
A setting that needs to be enabled is "Duplicate Strings", it allows two identical sentences to only be counted as one. This reduces the total word count and therefore costs. 

To enable this you need to go into the "settings" tab at the very right.

<img src="README_pics/Screenshot_20260720_140218.png" width="400" height="800" />

Then scroll down to the "import" bar and select it.

<img src="README_pics/Screenshot_20260720_140247.png" width="300" height="600" />

After that look to the right to find the "duplicate strings" menu select the "Hide (strict detection)" option.

<img src="README_pics/Screenshot_20260720_140338.png" width="1000" height="2000" />

Next select "Skip tags" under "Word and character count". This setting also reduces the word count by not allowing data tags to be marked as words.

<img src="README_pics/Screenshot_20260720_140405.png" width="500" height="1000" />


# How to Use
### Submitting
All submissions should be put into the "main" branch of the Github repositorysitory, and should be added into the following locations based on their types. 

###### Documents
All documents need to be submitted in English, as Crowdin will handle all translations to non-English languages. All documents should be in .fodt format and should only be added (or modified) in `docs-en/fodt/(app builder name)/(file)` for example `"docs-en/fodt/SAB/Scripture-App-Builder-01-Installation-Instructions.fodt".`

###### Images
In this repository images are handled differently than most other documentation repositorys. Images are not inserted into the documents themselves, but instead are inserted as links pointing to separate image files. This means that every document has a folder next to it that contains all the images displayed in that document. For example "Scripture-App-Builder-01-Installation-Instructions.fodt" would be next to a folder named SAB01, this folder would have all the images the document would use. More examples of this would be "Dictionary-App-Builder-04-Distributing-Apps.fodt" DAB04, "Reading-App-Builder-07-Using-aeneas-for-Audio-Text-Synchronization.fodt" RAB07.

<img src="README_pics/Screenshot_20260715_151502.png" width="300" height="600" />
<img src="README_pics/Screenshot_20260722_161042.png" width="300" height="600" />
<img src="README_pics/Screenshot_20260722_161127.png" width="300" height="600" />

The reason why this repository uses this system is that it makes it incredibly easy to switch out images in a document. Since screenshots containing English text can not be translated by Crowdin the next best solution is to replace these screenshots with ones containing text in the correct language. The Github workflow will automatically replace the screenshots, however the user still needs to manually supply all screenshots. The images are located in images/(language)/(app builder name)/(image folder) for instance "images/en-US/KAB/KAB02" and do not need to conform to a specific file format. Simply drop the images into the correct folder and the workflow will handle the rest.



### Workflow

1. Scroll to the top of the webpage and click on the actions tab at the top of the screen. Then click on the "auto translate" button under the green button labeled "new workflow". 

<img src="README_pics/Screenshot_20260723_112417.png" width="700" height="1000" />

2. Find the "run workflow" button on the right side of the screen and select the dropdown menu. Click the "Run workflow" option.

<img src="README_pics/Screenshot_20260713_155959.png" width="700" height="1000" />

3. The workflow is now running in the background. You can click the "Convert" button to view the output of the workflow. Or when the workflow has finished click "Summary" to view the artifact outputs.

<img src="README_pics/Screenshot_20260713_160239.png" width="700" height="1000" />



### Outputs
The workflow will produce two types of outputs. First it will generate all the translated files and add them to the "translations" branch. The user has the option to merge the translations branch into the main branch, if they want the new documents to be easily accessible.

The second output is a .zip artifact composed of PDFs from both English and non-English languages, this can be found by going to the workflow and clicking the "Summary" button.

# Conclusion


