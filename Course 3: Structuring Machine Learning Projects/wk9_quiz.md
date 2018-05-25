### Week 9 Quiz - Autonomous driving (case study)

1. Question 1
You are just getting started on this project. What is the first thing you do? Assume each of the steps below would take about an equal amount of time (a few days).

    [x] Spend a few days training a basic model and see what mistakes it makes.

2. Question 2    
Your goal is to detect road signs (stop sign, pedestrian crossing sign, construction ahead sign) and traffic signals (red and green lights) in images. The goal is to recognize which of these objects appear in each image. You plan to use a deep neural network with ReLU units in the hidden layers.

For the output layer, a softmax activation would be a good choice for the output layer because this is a multi-task learning problem. True/False?
    
    [x] False
    
3. Question 3    
You are carrying out error analysis and counting up what errors the algorithm makes. Which of these datasets do you think you should manually go through and carefully examine, one image at a time?

    [x] 500 images on which the algorithm made a mistake

4. Question 4    
After working on the data for several weeks, your team ends up with the following data:

- 100,000 labeled images taken using the front-facing camera of your car.
- 900,000 labeled images of roads downloaded from the internet.

Each image’s labels precisely indicate the presence of any specific road signs and traffic signals or combinations of them. For example, y(i) = [1 0 0 1 0] means the image contains a stop sign and a red traffic light.
Because this is a multi-task learning problem, you need to have all your y(i) vectors fully labeled. If one example is equal to [0 ? 1 1 ?] then the learning algorithm will not be able to use that example. True/False?

    [x] False

5. Question 5    
The distribution of data you care about contains images from your car’s front-facing camera; which comes from a different distribution than the images you were able to find and download off the internet. How should you split the dataset into train/dev/test sets?

    [x] Choose the training set to be the 900,000 images from the internet along with 80,000 images from your car’s front-facing camera. The 20,000 remaining images will be split equally in dev and test sets.
    
6. Question 6    
Assume you’ve finally chosen the following split between of the data:

- Training	940,000 images randomly picked from (900,000 internet images + 60,000 car’s front-facing camera images)	8.8%
- Training-Dev	20,000 images randomly picked from (900,000 internet images + 60,000 car’s front-facing camera images)	9.1%
- Dev	20,000 images from your car’s front-facing camera	14.3%
- Test	20,000 images from the car’s front-facing camera	14.8%

You also know that human-level error on the road sign and traffic signals classification task is around 0.5%. Which of the following are True? (Check all that apply).
    
    [x] You have a large data-mismatch problem because your model does a lot better on the training-dev set than on the dev set.
    [x] You have a large avoidable-bias problem because your training error is quite a bit higher than the human-level error.
    
7. Question 7    
Based on table from the previous question, a friend thinks that the training data distribution is much easier than the dev/test distribution. What do you think?

    [x] There’s insufficient information to tell if your friend is right or wrong.
    
8. Question 8    
You decide to focus on the dev set and check by hand what are the errors due to. Here is a table summarizing your discoveries:

- Overall dev set error	14.3%
- Errors due to incorrectly labeled data	4.1%
- Errors due to foggy pictures	8.0%
- Errors due to rain drops stuck on your car’s front-facing camera	2.2%
- Errors due to other causes	1.0%

In this table, 4.1%, 8.0%, etc.are a fraction of the total dev set (not just examples your algorithm mislabeled). I.e. about 8.0/14.3 = 56% of your errors are due to foggy pictures.

The results from this analysis implies that the team’s highest priority should be to bring more foggy pictures into the training set so as to address the 8.0% of errors in that category. True/False?
    
    [x] False because this would depend on how easy it is to add this data and how much you think your team thinks it’ll help.
   
9. Question 9    
You can buy a specially designed windshield wiper that help wipe off some of the raindrops on the front-facing camera. Based on the table from the previous question, which of the following statements do you agree with?

    [x] 2.2% would be a reasonable estimate of the maximum amount this windshield wiper could improve performance.

10. Question 10    
You decide to use data augmentation to address foggy images. You find 1,000 pictures of fog off the internet, and “add” them to clean images to synthesize foggy days, like this:

Which of the following statements do you agree with? (Check all that apply.)
    
    [x] So long as the synthesized fog looks realistic to the human eye, you can be confident that the synthesized data is accurately capturing the distribution of real foggy images, since human vision is very accurate for the problem you’re solving.

11. Question 11    
After working further on the problem, you’ve decided to correct the incorrectly labeled data on the dev set. Which of these statements do you agree with? (Check all that apply).
    
    [x] You should also correct the incorrectly labeled data in the test set, so that the dev and test sets continue to come from the same distribution
    [x] You should not correct incorrectly labeled data in the training set as well so as to avoid your training set now being even more different from your dev set.
    
12. Question 12    
So far your algorithm only recognizes red and green traffic lights. One of your colleagues in the startup is starting to work on recognizing a yellow traffic light. (Some countries call it an orange light rather than a yellow light; we’ll use the US convention of calling it yellow.) Images containing yellow lights are quite rare, and she doesn’t have enough data to build a good model. She hopes you can help her out using transfer learning.

What do you tell your colleague?
    
    [x] She should try using weights pre-trained on your dataset, and fine-tuning further with the yellow-light dataset.

13. Question 13
Another colleague wants to use microphones placed outside the car to better hear if there’re other vehicles around you. For example, if there is a police vehicle behind you, you would be able to hear their siren. However, they don’t have much to train this audio system. How can you help?

    [x] Neither transfer learning nor multi-task learning seems promising.
    
14. Question 14    
To recognize red and green lights, you have been using this approach:

- (A) Input an image (x) to a neural network and have it directly learn a mapping to make a prediction as to whether there’s a red light and/or green light (y).

A teammate proposes a different, two-step approach:

- (B) In this two-step approach, you would first (i) detect the traffic light in the image (if any), then (ii) determine the color of the illuminated lamp in the traffic light.
Between these two, Approach B is more of an end-to-end approach because it has distinct steps for the input end and the output end. True/False?

    [x] False
    
15. Question 15    
Approach A (in the question above) tends to be more promising than approach B if you have a ________ (fill in the blank).

    [x] Large training set
