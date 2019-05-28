Link to original repository: https://github.com/JLaoo/Classifying-Waifus-via-Transfer-Learning

# Classifying Waifus via Transfer Learning

Based off of Freedomofkeima's blog post found here: https://freedomofkeima.com/blog/posts/flag-15-image-recognition-for-anime-characters

# Steps

1) scrape_images.ipynb
- Scrapes images from the first 3 pages of search results for the wanted characters via safebooru (not tryna get banned lmao).
- Saves these images in local directories.
2) detect_faces.ipynb
- Using nagadomi's lbpcascade_animeface (https://github.com/nagadomi/lbpcascade_animeface) we can detect faces and save the cropped results to yet another local directory.
3) resize_cropped.ipynb
- Resizes all of the images into 96x96 squares. Not sure if this step is actually ncessary since TensorFlow resizes images anyways, but I didn't think that far ahead at this step.
- I had to manually clean the resized images after this step since lbpcascade_animeface isn't 100% accurate and some pictures contained multiple faces.
4) split_dataset.ipynb
- Splits images into training and test sets. My dataset really wasn't that large so most inaccuracies in the model can probably be attributed to the lack of data.
- For each character, I had 85% (rounded down) of their faces as training data and the rest as test data.
5) modeling.ipynb
- Trained with 20 epochs at first, got like 60% accuracy probably due to overfitting. Changed it to 10 epochs and got >90% accuracy.
- Again, the lack of data is the biggest limitation at this step, but nothing I can do about that :/

As we can see below, the accuracy for the training set is very high!
![30 predictions in the test set](https://i.imgur.com/QhkGtfl.png)

The accuracy for the test set is not as high, but still respectable!
![30 predictions in the training set](https://i.imgur.com/e8UwVDB.png)

# Remarks
Overall a fun little project that I enjoyed working on. I chose New Game! since it's probably the closest there is to an anime about software engineering. Got familiar with TensorFlow (I had only used SKLearn before this) and also got my first taste of neural nets.

# To do
- Increase size of dataset.
- Tune hyperparameters.
