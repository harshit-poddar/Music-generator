# Music-generator

### Problem Statement :
- We are using LSTM model for training sequential data that we have made after extracting notes and chords from 100 midi files using music21 trained with three layer for 100 epochs.

### Data Description
-  We are extracting notes and chords from music file and store it in container using music21 library. Actually it is list of list containing sequences of notes and chords.
{0.0} <music21.metadata.Metadata object at 0x25c372f9ad0>
{0.0} <music21.stream.Part 0x25c372fb150>
    {0.0} <music21.stream.Measure 1 offset=0.0>
        {0.0} <music21.instrument.Piano 'Staff: Piano'>
        {0.0} <music21.clef.TrebleClef>
        {0.0} <music21.tempo.MetronomeMark Quarter=95.0>
        {0.0} <music21.key.Key of D major>
        {0.0} <music21.meter.TimeSignature 4/4>
        {0.0} <music21.stream.Voice 0x25c37346f10>
            {0.0} <music21.note.Note A>
            {0.25} <music21.note.Rest 5/12ql>
            {0.6667} <music21.note.Note G>
            {1.1667} <music21.note.Rest 1/3ql>
            {1.5} <music21.note.Note D>
            {1.8333} <music21.note.Rest 1/6ql>
            {2.0} <music21.note.Note A>
            {2.25} <music21.note.Rest 16th>
            {2.5} <music21.note.Note G>
            {2.8333} <music21.note.Rest 1/6ql>
            {3.0} <music21.note.Note D>
            {3.25} <music21.note.Rest 16th>
            {3.5} <music21.note.Note A>
            {3.8333} <music21.note.Rest 1/6ql>
        {0.0} <music21.stream.Voice 0x25c3737c7d0>
            {0.0} <music21.note.Note A>
            {0.3333} <music21.note.Rest 2/3ql>
            {1.0} <music21.note.Note F#>
            {1.25} <music21.note.Rest eighth>
            {1.75} <music21.note.Note C#>
            {2.0833} <music21.note.Rest 2/3ql>
            {2.75} <music21.note.Note F#>
            {3.0833} <music21.note.Rest 2/3ql>
            {3.75} <music21.note.Note D>

### Data generation for model training.

We have preprocessed all the music files and combine it in one single list. Our list has 60,846 data points.
 
 ##### - Prepare Sequential data for LSTM
 We have created a map between unique notes in list with their indices that can be used to create label for our supervised data generation.
 We have created sequential data with 100 datapoints in each sequence from our list and store 101 datapoint as its output. We are storing mapped value of each element for our network input and output. We will then normalised our data for model training. Since output can range between 398 unique classes. We have done one hot encoding on our output data.




### Model Training 
We have used three layers of LSTM and softmax as its activation function. We have trained our model on input data for 100 epochs.

### Prediction 
We are using the reverse approach we used in pur training for generating music file using our model. For music generation here we take 200 datapoint. We have taken 100 sequences for each datapoint and predict its output using our model. Since we are using softmax it will give you the probability for 398 classes we are taking maximum among the output as label for our generated music datapoint We then convert the prediction output in a midi file. 



