# Project: Classify Celebrity Faces!


What to do: Create Custom Vision Resource, Create new project, download images, train model, test model

Time to complete: 1 hour<br>
Operating System Requirement: None<br>
Other Requirements: Verified Student Email Account <br>

Target Audience: 12-14 years old <br>

Learning Goals: 
* Gain exposure to using Azure Custom Vision 
* Gain basic understanding of machine learning pipeline

## Part 0: Introduction
Howdy partner! You must be a humon! Welcome to Azure, the frontier of cloud technology! It is a mystical realm filled with things only from the imagination: giant virtual machines, vast data lakes, and more! Really, anything you can think of computer-related, you'll probably find it in this world. 

Today, we're going to explore one of the wonders of Azure: Custom Vision API. It is a structure that extracts the essence of something called ```machine learning``` and converts it into a tool for humons to use, or a ```model```. Humons can then use that model to find anything they want from any photos they throw at it. Ready to learn about this wonder? Oops, ready or not, here we goo!!!!

First of all, what is this Azure we speak of? Well, it's technically a service, but really it's an endless world of possibilities. You can do any computer-techie-amazingly-geeky-related thing you can possibly think of in Azure! Azure exists on and uses something that we call ```the Cloud```.

<img src="images/clouds.jpg">

No, not that cloud! The Cloud we're talking about doesn't physically float in the sky, but rather, floats in cyberspace. Like iCloud and Azure, Cloud simply means "not at your physical computer, but on someone elses". The only way we can talk to these remote computers is through the internet.

We'll be using  ```resources```, or structures in the realm of Azure, to help us identify the faces of different humon celebrities using the essence of ```machine learning```.

What is ```machine learning```? Well, to put it simply, it's a technique to predict future data given past data. In Azure, we view machine learning as tools like hammers and nails are to humons. It's super cool because it is one of the building blocks to artificial intelligence!

Examples of what you can do with machine learning include having a computer learn to play Snake by itself through trial and error, predict whether or not it's going to rain today based off past weather patterns, and more. It's pretty awesome!! The best thing is: humons can use it too! Weee!!

We'll use one of the wonders of Azure, the Custom Vision API, to extract machine learning essence and do some cool things with it. Wow, it's been a while since I've visited that place; I hope they still recognize my face!!!

Now, let's get some of 'em machine learning essence to try and identify celebrities based off pictures of their faces!

## Part 1: Create Azure Student Account
First thing we want to do is get you a key to access the Azure realm. Note that it costs money to access Azure, but as a student you can do it for free; if that isn't enough incentive to go to school, I don't know what is! Go and create an Azure Student account. If you already have an Azure Student account, skip to Part 2. Otherwise, follow these steps:<br>
1. Go to this link: https://azure.microsoft.com/en-us/free/students/
2. Click ```Activate Now```
3. Click ```Use Another Account```
4. Create a new account

Now, you should have a new key! Good job humon.

## Part 2: Log into Azure Student Account
Let's enter the portal with our key now:
* https://azure.microsoft.com/en-us/

Once you've logged in, click ```Portal``` on the top right of your screen.

<img src="images/azure_portal_button.png" width="500" height="350">

The ```Portal``` is the gateway that connects the humon world with the realm of Azure. Onward!!

## Part 3: Create Custom Vision Resource
Our next step should be to create a new Custom Vision resource. What was that? You thought that the Custom Vision API was a wonder, and you're confused why you're creating a new one? Well, you're not creating a new Custom Vision API, but rather, using the wonder to create a new structure called a ```model```. That model we're creating is going to help us identify the celebrities! Remember, the Custom Vision API wonder is located in the Cloud, in the wondrous lands of Azure. 

Let's get started shall we? Hit ```Create a Resource``` on the top left of your screen.

<img src="images/create_a_resource.png" width="20%" height="20%">

In the magical search bar, type in ```Custom Vision``` and hit enter. It should bring you to this:

<img src="images/custom_vision_download.png">

Click ```Create```, and enter these settings. 
* Remember: for ```Resource Group```, if "CelebrityClassifier" doesn't exist already, just click ```Create new``` and enter it.

<img src="images/custom_vision_settings.png">

Hit ```Create```.

Congratulations! You've successfully deployed your first ```Custom Vision``` resource! Now, the fun part: we wait. Yeahh, you thought that we could just enter another dimension with the snap of the finger? Well, I guess you did, but we still have to wait... What was that? No, we're not there yet! 

## Part 4: Log into Custom Vision Portal
Next, we need to travel to the wonder. There, we shall construct our own model to recognize faces!

Here's the gate to our destination:
* https://www.customvision.ai/

Click ```Sign in```, and sign into your Student account.

## Part 5: Create a Project
Congratulations, you're at the Custom Vision API! Let's create a new project. Click the button that says ```New Project```

<img src="images/new_project.png" width="50%" height="50%">

Next, copy the settings below.

<img src="images/project_settings.png" width="40%" height="40%">

You might be curious as to what we just input. Let's break it down:

<img src="images/project_settings_explanation.png" width="40%" height="40%">

Geez, they sure do want a lot, don't they? I just want to start classifying images!!

## Part 6: Preparing Data
If you followed the above steps correctly, you should see this:

<img src="images/default_custom_vision_screen.png">

This is our workspace to upload data and train our classification model! Looks beautiful right? I think I might be crying... Okay that's enough! 

Remember, to properly use the essence of ```machine learning```, we need to first throw a bunch of data at our machine before it can predict anything. Data can exist in many forms; in this case, different images of our celebrities will be our data. 

To start, let's upload our data! Download this file:
* [celebs.zip](https://mspimageclassification.file.core.windows.net/images/celebs.zip?sp=rl&st=2019-11-11T03:46:58Z&se=2019-11-12T03:46:58Z&sv=2019-02-02&sig=us1mfWTZrNR2%2Fh5ELuD%2BnRJzi2iSVFZreVQ2SdUNDag%3D&sr=f)

This should download a file called ```celebs.zip``` on your computer. Go to your ```Downloads``` on your computer and unzip the file you just downloaded. You can do this typically by right clicking ```celebs.zip``` and select ```Extract All```; if you're on Mac, just double clicking the .zip file will do.
  
You should be left with 4 folders: elon, kim, scarlett, and tests.

To break this down, the folders ```elon```, ```kim```, and ```scarlett``` each contain 5 face photos of Elon Musk, Kim Kardashian, and Scarlett Johansson, respectively. These photos are what we'll be using as data for our machine learning model. The folder ```tests``` contains all the images that we'll test against our model to see just how accurate our model is.

Before we can train a model that can recognize what each image is, we have to tell it what each image is in our training dataset. To do this, we use something called ```tags``` to label our images.
   
Go back to Custom Vision API, and click the ```+``` icon to the right of ```Tags```

<img src="images/tag_plus_icon.png" width="30%" height="30%">

You should see a pop-up now. This will be how we create new tags to label our data before training our model! 

For our first tag, we need to think of something to characterize our images. In this case, since they are all celebrities, enter ```celebrity``` and hit ```Save```.

If you notice on the left hand side, we now have a tag called ```celebrity```. This thing must be magical or something! Repeat this process and add the following tags:
* elon
* kim
* scarlett

You should now see four tags on the left hand side of your screen:

<img src="images/four_celeb_tags.png" width="30%" height="30%">

You can add as many tags as you want to describe tags; each one you add is just one parameter to identify the images with. Hey... hey! Elon isn't a "tesla", so why are you labeling him as one? Arghhh, fine so be it.

## Part 7: Uploading Data
You've come far, adventurer! Stay with me, we're almost there.

Our last step in preparations is to upload our images and tag them. Hit the ```Add Images``` button on the top left corner:

<img src="images/add_images.png" width="50%" height="50%">

Navigate to ```elon``` and select all 5 images in the folder. While it's uploading, we can tag these 5 photos with their appropriate labels. In the box that says ```Add a tag and press enter```, add the tags: ```celebrity``` and ```elon```. Your screen should look like this:

<img src="images/elon_images.png" width="50%" height="50%">

Hit ```Upload```, and wait until you get a success screen. Go ahead and repeat Part 7 until you've finished uploading and labeling ```kim``` and ```scarlett```. Make sure to label them appropriately! Don't label a Kim as a ```scarlett```!
* Kim photos should be labeled ```celebrity``` and ```kim```
* Scarlett photos should be labeled ```celebrity``` and ```scarlett```

Your final screen should look like this:

<img src="images/all_images.png">

## Part 8: Training Model
Now, the fun part: training our model! I know, about time too!

Training our model will teach it how to recognize whether a photo is of Kim, Elon, or Scarlett. The more data we throw at it, the more accurate it gets.

Click on the green ```Train``` button on the top right of your screen.

<img src="images/train_button.png" width="60%" height="60%">

Choose ```Quick Training``` and hit ```Train```. Then, we wait about half a minute for our model to train. Yeah yeah, half a minute ain't too bad so just wait it out!!

## Part 9: Testing Model
Once our model is finished training, we have a fully functional ```machine learning``` model that can classify images for us! More specifically for us, it should be able to tell the differences among images of Elon, Kim, and Scarlett.

At this point, you must be pretty skeptical about this whole machine learning business. I'm betting you want to see it in action already... Well, lucky you!

To test that our model actually works, we can throw a few photos at our model for it to classify. Click the ```Quick Test``` button right next to the ```Train``` button.

<img src="images/quick_test_button.png" width="60%" height="60%">

Then, let's upload one image at a time to test. Select ```Browse local files```, and navigate to ```tests```. Upload ```scarlett_test.jpg```. 

<img src="images/scarlett_test_result.png">

Notice on the bottom right corner, our model this image to most likely be type ```celebrity``` and ```scarlett```. Mission success!! It's almost like magic... no I'm not crying!

Go ahead and do the same for Elon and Kim, and see how they go. 

Last but not least, try uploading that cute looking kitty you see in ```tests``` as well.  What do you observe from the percentages on the kitty? Why do you think our model believes the kitty looks the most like Scarlett?

Go ahead and try uploading any other ```face``` photo you find on the internet against your model! (i.e. Try searching ```Taylor Swift face```)
See if you can figure out the answer to the question above based off your new findings. 

If you don't know it, we'll try and answer the question together later... what, you want the answer now? Go try it out yourself first, and then come back to me! Plus, I'm busy wiping away these tears... no, I'm not crying!! 

## Part 10: Create Your Own Model
Slow down, adventurer! I gotta learn you a thing or two first.

Before we continue, you may have noticed that if you upload faces with similar skin tones to  a celebrity (for example, Kim), your model will predict those faces to be Kim. This is because our model doesn't have enough images to be completely accurate yet! Actually, a big part of our model relies on the ```colors``` in the images. Thus, our model must've noticed that the images we uploaded of Scarlett were most similar to the kitty's. 

Remember, the more data we throw at our model, the more accurate it becomes. Now this doesn't mean throw bad data at it, like label ```Kim``` photos as ```elon```. That'll just ruin our model! 

Now, let's try creating your own model to predict faces of your favorite celebrities!
Pick out 3 celebrities of your choice (i.e. Kevin Hart). Then, search on ```Google Images```
for a few ```face``` images of each celebrity, and download it.

* Note: It's really important to add ```face``` to your search! You only want to train images
of their faces, not their bodies or backgrounds.

Pick out a few test images of each celebrity like we did with the celebrities. Then, follow
the steps beginning at Part 5, except with your own photos!

To get started, hit the ```eye``` icon on the top left corner of your model.

<img src="images/eye.png" width="10%" height="10%">

Move on to Part 12 once you've successfully created another model. Isn't this exciting? No wonder this place is a wonder of Azure!

## Part 11: Clean Up
Wow, that was a lot of fun! Unfortunately buddy, we gotta head back home! Before we do so, we need to clean up what we've just created, or else we'll have to pay up in gold. And no one wants to give up gold for free, now do they?

To clean up, first click the ```eye``` icon on the top left of our Custom Vision API. Then, hit the trash icon next to our projects.

Then, go to the Azure portal, and click ```Resource Groups``` on the left hand side. Click on ```CelebrityClassifier```, and hit the ```Delete resource group``` on the top. Go ahead and type in the resource group's name and hit ```Delete```.

Do the same thing for any other resource groups you created.

You should be cleaning up your resources as often as you clean up your room. Wait, who said that they don't clean their own room?

## Part 12: Recap
Whew, we made it back home! What did you think about that adventure, adventurer? Today, we explored one of the wonders of the realm of Azure: Custom Vision API. We saw the power of this wonder in action, and how it collected the essence of ```machine learning``` to build a model that could recognize individual faces. 

Isn't that the most amazing thing you've ever seen?? I promise I'm not about to cry again...

Now, a question you might be asking yourself is how can humons use this resource. The answer is in an infinite amount of ways! The possibilities are endless! 

* If you want to create a model to recognize each and every one of your family members, go start a project and impress your parents.
* You can combine Custom Vision API with other wonders of Azure to build fancy structures like image classifying web applications that also exist in the cloud! 
* If you do research in machine learning or need image classification tools for other research, Azure's Custom Vision API is perfect for your needs! You don't need much data to create a very accurate model.
* and a lot lot lot more!!!

I hope today was fun, because I had a lot of fun! *sniff* I just wanted to say congratulations adventurer. Azure is a realm of mystery and power, but can be sometimes hard to navigate unless you're a seasoned veteran. You are a champion!

Until we meet again, so long humon! Weeee!!!!
