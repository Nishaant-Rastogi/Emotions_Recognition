# Emotion Classification from RAVDNESS Dataset

**Executive Summary**

This project presents a deep learning classifier able to predict the emotions of a human speaker encoded in an audio file. The classifier is trained using the RAVDESS dataset, and has an overall F1 score of 80% on 8 classes (neutral, calm, happy, sad, angry, fearful, disgust and surprised).

**Feature set information**

For this task, the dataset is built using:

- the [Ryerson Audio-Visual Database of Emotional Speech and Song (RAVDESS) dataset](https://zenodo.org/record/1188976#.XsAXemgzaUk)

The samples include:

- 1440 speech files and 1012 Song files from **RAVDESS**. This dataset includes recordings of 24 professional actors (12 female, 12 male), vocalizing two lexically-matched statements in a neutral North American accent. Speech includes calm, happy, sad, angry, fearful, surprise, and disgust expressions, and song contains calm, happy, sad, angry, and fearful emotions. Each file was rated 10 times on emotional validity, intensity, and genuineness. Ratings were provided by 247 individuals who were characteristic of untrained adult research participants from North America. A further set of 72 participants provided test-retest data. High levels of emotional validity, interrater reliability, and test-retest intrarater reliability were reported. Validation data is open-access, and can be downloaded along with our paper from [PLoS ONE](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0196391).

**Metrics**

_Loss and accuracy plots_

![Link to loss](https://github.com/Nishaant-Rastogi/Emotions_Recognition/blob/main/media/model_loss.png)

![Link to accuracy](https://github.com/Nishaant-Rastogi/Emotions_Recognition/blob/main/media/model_accuracy.png)

_Classification report_

![Link do classification report](https://github.com/Nishaant-Rastogi/Emotions_Recognition/blob/main/media/classification_report.png)

_Confusion matrix_

![Link do classification report](https://github.com/marcogdepinto/Emotion-Classification-Ravdess/blob/master/media/ConfusionMatrix.png)

**How to use the code inside this repository**

1.  Download Audio_Song_Actors_01-24.zip and Audio_Speech_Actors_01-24.zip, unzip and merge the content of the folders (e.g. Actor_01 should include both Speech and Song).

2.  Run the VideoToWav.py script to convert video to audio wav files and then add it to the `features` folder.

3.  The Jupyter Notebook `EmotionsRecognition.ipynb` is present in the `legacy_code/` folder. Run all the cells and the model will be created in the `model` folder

    **How to test the model created in this work**

Let's be clear. When we talk about emotions understanding, we are talking about a very difficult task.

I have pasted two files in the `examples` folder:

a) 03-01-01-01-01-02-05.wav is an example of WRONG prediction: it is a NEUTRAL file, the model predicts CALM. Try to listen to the audio yourself. Which is the emotion for you? For me CALM seems a fair prediction. That speaker is classified as neutral, but he is not angry at all. You see my point?

b) 10-16-07-29-82-30-63.wav is a DISGUST file. The model is getting it.

Feel free to try with other files or record your voice. I still have to try this last one but I am very curious about the result.

_Important note_: the classes are encoded from 0 to 7 in the code. In the dataset, from 01 to 08. Be aware when you try. If the model predicts 0 and you are using a NEUTRAL file (01), this is correct and the expected behavior. Keras wants the predictions to start from 0 and not from 1, so the code is adjusted to cope with this requirement.
