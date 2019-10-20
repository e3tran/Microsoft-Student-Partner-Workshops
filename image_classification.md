# Project: Classify Celebrity Faces!


What to do: Create Custom Vision Resource, Create new project, download images, train model, test model, save dockerfile on Azure Storage Resource

Time to complete: 1 hour<br>
Operating System Requirement: None<br>
Other Requirements: Verified Student Email Account <br>

Learning Goals: 
* Gain exposure to using Azure Custom Vision and Azure Storage Resource
* Gain basic understanding of machine learning pipeline
* Learn importance of directories and files

## Part 0: Introduction
First of all, what is Microsoft Azure? Azure is a Cloud Computing Service, but really 
it'll do almost anything computer-related that you could possibly think of! Its services
are hosted through something called ```the Cloud```.

<img src="images/clouds.jpg">

No, not that cloud! The Cloud we're talking about doesn't physically float in the sky, but
rather, floats in cyberspace. Like iCloud and Azure Services, Cloud simply means "not at
your physical computer, but on someone elses". The only way we can talk to these remote
computers is through the internet.

In this workshop, we'll be using Azure's Cloud services, or ```resources```, to help us identify the faces of different
NBA stars through a Computer Science technique called ```machine learning```. 

What is ```machine learning```? Well, to put it simply, it's the process of throwing a bunch
of data at a computer so that the computer can predict what future data will look like. It's
super cool because it's almost like artificial intelligence!

One example of machine learning is having a computer learn how to play Snake by itself
through trial and error. Another example is having a computer predict whether or not
it's going to rain today based off wind patterns. It's pretty awesome!!

Today, we'll be using machine learning to identify celebrities based off pictures of their faces.
We'll use NBA Stars as an example; then, you will pick your own celebrities to train a model off of!

## Part 1: Create Azure Student Account
First thing we want to do is create an Azure Student account. If you already have an Azure Student account, 
skip to Part 2. Otherwise, follow these steps:<br>
1. Go to this link: https://azure.microsoft.com/en-us/free/students/
2. Click ```Activate Now```
3. Click ```Use Another Account```
4. Create a new account

## Part 2: Log into Azure Student Account
Now that you should have your own Student account, let's log in:
* https://azure.microsoft.com/en-us/

Once you've logged in, click ```Portal``` on the top right of your screen.

<img src="images/azure_portal_button.png" width=500 height=350>

The ```Portal``` is our main way to use Azure's different Cloud resources.

## Part 3: Create Custom Vision Resource
Our next step should be to create a new Custom Vision resource. This Azure Cloud service 
specializes in classifying images based off their labels, using ```machine learning```.
By using the ```Custom Vision``` resource, we will rent Microsoft's supercomputers to classify NBA stars.

Hit ```Create a Resource``` on the top left of your screen.

<img src="images/create_a_resource.png" width=20% height=20%>

In the search bar, type in ```Custom Vision``` and hit enter. It should bring you to this webpage:

<img src="images/custom_vision_download.png">

Click ```Create```, and enter these settings. 
* Note: for ```Resource Group```, if "NBAClassifier" doesn't exist already, just click ```Create new``` and enter it.

<img src="images/custom_vision_settings.png" width=30% height=30%>

Hit ```Create```.

Congratulations! You've successfully deployed your first ```Custom Vision``` resource! 
Now, the fun part: we wait. Once it's deployed successfully, feel free to move on to Part 4.

## Part 4: Log into Custom Vision Portal
Next, we need to access a separate portal dedicated to the ```Custom Vision``` resource.
Like the Azure portal, the Custom Vision portal is how we work with the Custom Vision resource.
To start, let's go to this link:
* https://azure.microsoft.com/en-us/services/cognitive-services/custom-vision-service/

Click ```Get Started```, and sign into your Student account.

<img src="images/get_started_custom_vision.png">

## Part 5: Create a Project
Congratulations, you're in! Let's create a new project! Click the button that says ```New Project```

<img src="images/new_project.png" width=50% height=50%>

Next, copy the settings below.

<img src="images/project_settings.png" width=40% height=40%>

You might be curious as to what we just input. Let's break it down:

<img src="images/project_settings_explanation.png" width=40% height=40%>

## Part 6: Preparing Data
If you followed the above steps correctly, you should see this screen:

<img src="images/default_custom_vision_screen.png">

This is our workspace to upload data and train our classification model!

To start, let's upload our data! Download this file:
* [nba.zip](https://imageclassifier.file.core.windows.net/nbastars/nba.zip?sp=rl&st=2019-09-26T22:10:09Z&se=2022-07-19T22:10:00Z&sv=2018-03-28&sig=b998Q28PQivrilJtQ58d%2BHeBgll%2FebmoTUiG99gljzg%3D&sr=f)

This should download a file called ```nba.zip``` on your computer. Go to your ```Downloads``` on your
computer and unzip the file you just downloaded. You can do this typically by right clicking
```nba.zip``` and select ```Extract All```; if you're on Mac, just double clicking the .zip file will do.
  
You should be left with a folder called ```nba```, which contains 4 more folders: kobe, lebron, steph, and tests.

To break this down, the folders ```kobe```, ```lebron```, and ```steph``` each contain
5 face photos of NBA stars Kobe Bryant, Lebron James, and Stephen Curry, respectively.
These photos are what we'll be using as data for our ```machine learning``` algorithms. 
In fancier terms, we will using these images to train a ```machine learning``` model that 
will classify our images. The folder ```tests``` contains all the images that we'll test 
against our model to see how accurate it really is.

Before we can train a model that can recognize what each image is, we have to tell it
what each image is in our training dataset. To do this in Azure, we use something called
```tags``` to label our images.
   
Go back to your Custom Vision Portal, and click the ```+``` icon to the right of ```Tags```

<img src="images/tag_plus_icon.png" width=30% height=30%>

You should see a pop-up now. This will be how we create new tags to label our data before training our model!

For our first tag, we need to think of something to characterize our images. In this
case, since they are all NBA players, enter ```player``` and hit ```Save```.

If you notice on the left hand side, we now have a tag called ```player```! Repeat this process and add the following tags:
* kobe
* lebron
* steph

You should now see four tags on the left hand side of your screen:

<img src="images/four_nba_tags.png" width=30% height=30%>

You can add as many tags as you want to describe tags; each one you add is just one
parameter to identify the images with.

## Part 7: Uploading Data
Our last step in preparations is to upload our images and tag them! Hit the ```Add Images``` button on the top left corner:

<img src="images/add_images.png" width=50% height=50%>

Navigate through ```nba``` -> ```kobe```, and select all 5 images in the folder. While it's uploading, we can
tag these 5 photos with their appropriate labels. In the box that says ```Add a tag and press enter```,
add the tags: ```player``` and ```kobe```. Your screen should look like this:

<img src="images/kobe_images.png" width=50% height=50%>

Hit ```Upload```, and wait until you get a success screen. Go ahead and repeat Part 7
until you've finished uploading and labeling ```lebron``` and ```steph```. Make sure to
label them appropriately! Don't label a Kobe as a ```lebron```!
* Lebron photos should be labeled ```player``` and ```lebron```
* Steph photos should be labeled ```player``` and ```steph```

Your final screen should look like this:

<img src="images/all_images.png">

## Part 8: Training Model
Once you've uploaded all the photos, it's time to train our model!

Click on the green ```Train``` button on the top right of your screen.

<img src="images/train_button.png" width=60% height=60%>

Choose ```Quick Training``` and hit ```Train```. Then, we wait about half a minute for
our model to train!

## Part 9: Testing Model
Once our model is finished training, we have a fully functional ```machine learning``` model
that can classify images for us! More specifically for us, it should be able to tell
the differences among images of Kobe, Lebron, and Steph.

To test that our model actually works, we can throw a few photos at our model for it to
classify. Click the ```Quick Test``` button right next to the ```Train``` button.

<img src="images/quick_test_button.png" width=60% height=60%>

Then, let's upload one image at a time to test. Select ```Browse local files```, and
navigate to ```nba``` -> ```tests```. Upload ```steph_test.png```. 

<img src="images/steph_test_result.png">

Notice on the bottom right corner, our model this image to most likely be type
```player``` and ```steph```. Mission success!

Go ahead and do the same for Lebron and Kobe, and see how they go. 

Last but not least, try uploading that funny looking cat you see in ```tests``` as well. 
What do you observe from the percentages on the cat? Why do you think Kobe has
the highest similarity percentage compared to Lebron and Steph?

Go ahead and try uploading any other ```face``` photo you find on the internet against your model! (i.e. Try searching ```kobe bryant face```)
See if you can figure out the answer to the question above based off your new findings. 

## Part 10: Create Your Own Model
Before we continue, you may have noticed that if you upload faces with similar skin tones to 
a player (for example, Kobe), your model will predict those faces to be Kobe.
This is because our model doesn't have enough images to be completely accurate yet! Actually,
a big part of our model relies on the ```colors``` in the images. Thus, our model
must've noticed that the images we uploaded of Kobe were most similar to Kitty Bryants'. 

Now, let's try creating your own model to predict faces of your favorite celebrities!
Pick out 3 celebrities of your choice (i.e. the Kardashians). Then, search on ```Google Images```
for a few ```face``` images of each celebrity, and download it.

* Note: It's really important to add ```face``` to your search! You only want to train images
of their faces, not their bodies or backgrounds.

Pick out a few test images of each celebrity like we did with the NBA stars. Then, follow
the steps beginning at Part 5, except with your own photos!

To get started, hit the ```eye``` icon on the top left corner of your model.
Make sure you don't delete the NBA project you created, we'll use it later!

<img src="images/eye.png" width=10% height=10%>

Move on to Part 11 once you've successfully created another model.

## Part 11: Storing Model
Once you're done playing with your model, we can store our model on Azure's ```Cloud Storage``` resource.
The Azure ```Cloud Storage``` resource is a way we can store files online, and also share
them with others. It's similar to ```Google Drive``` except that you can do a lot
more things as a developer!

To keep things simple, we'll be storing our NBA model that we created earlier. 
In order to create our storage resource, we need to rent space from Microsoft's supercomputers for our storage again.

In your Custom Vision Portal, navigate to your ```NBA Face Classifier```. Click the 
```Performance``` tab and hit ```Export```.

<img src="images/export_button.png" width=70% height=70%>

Then select ```Dockerfile``` so we can use your model in future Azure features. 

Choose ```Windows``` as a version, and hit ```Export```. Once the progress bar is gone, hit
```Download```.

Congratulations! You are now downloading your model. In the meantime, let's go back
to Azure Portal:
* https://azure.microsoft.com/en-us/

Hit ```Create a Resource``` on the top left of your screen, and navigate to 
```Storage```. You should see this page:

<img src="images/storage_account_page.png" width=70% height=70%>

Click on ```Storage account```. Then, input these settings:

<img src="images/storage_account_settings.png" width=70% height=70%>

Go ahead and create this resource. It should take about 10 seconds to deploy.

Once it's done, hit ```Go to resource```. If you can't find it, then you can
also navigate to your storage account on the left side of the screen at
```Resource groups``` -> ```NBAClassifier``` -> ```nbaclassifiermodel```.

Then, we want click the ```Files``` under ```Services``` to specify that you're going to upload a file. 

<img src="images/upload_file.png" width=80% height=80%>

Once you're inside, you should see a button ```File share```; it just creates a folder and asks you how big you want it. Click it and input these settings:
1. ( Pick a name for your folder )
2. 1 ( 1 gigabyte should be more than sufficient)
3. Create

Then, go into your folder and click ```Upload```, and upload your .zip file!!

## Part 12: Clean Up
To stop Azure from charging you more money, go to ```Resource Groups```, and check the box to the left
of ```NBAClassifier```. Click the 3 dots on the right hand side of the resource, and hit
```Delete resource group```. Go ahead and type in the resource group's name and hit ```Delete```. 

<img src="images/delete_resource_group.png">

Do the same thing for all other resource groups you see in the ```Resource Groups``` tab, until
you do not see any more resource groups in your ```Resource Groups``` tab.

In addition, go onto your Custom Vision Portal, and delete all the projects that you created:
* https://azure.microsoft.com/en-us/services/cognitive-services/custom-vision-service/
