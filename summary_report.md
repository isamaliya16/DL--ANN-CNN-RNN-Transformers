# Summary Report: Deep Learning Practical Exam (Set C)

## The Five Tasks and Datasets

1. **ANN:** Classified wines into three classes using the scikit-learn Wine dataset (178 wines, 13 features).
2. **OpenCV:** Processed five scikit-image pictures (astronaut, coffee, chelsea, rocket, colorwheel) with colour masks, morphology, Sobel edges and Haar face detection.
3. **CNN:** Recognised handwritten digits and compared a CNN with an ANN, using a subset of MNIST (20,000 train, 4,000 test).
4. **RNN:** Forecast daily minimum temperature with a GRU, using 3,650 days of Melbourne data (1981 to 1990).
5. **Transformers:** Used pre-trained Hugging Face models for fill-mask, question answering and text generation, with five paragraphs and ten questions I wrote.

## A New Concept and What I Learned

The new concept for me was the **feature map**. A Conv2D layer slides small filters over an image, and each filter produces a map showing where it found something, such as an edge or a stroke. Plotting the 16 maps of the first layer made this clear. It also explained why a CNN is smaller than an ANN: one 3 x 3 filter is reused over the whole image, so my CNN needed 56,714 parameters against 109,386 for the ANN.

I also learned the value of a **baseline**. Without the naive "tomorrow = today" forecast, I could not have judged the GRU.

## Results

- **ANN:** 94.44% test accuracy (2 of 36 wines wrong). Scaling mattered, because proline has a far larger range than the other features.
- **OpenCV:** The orange mask kept the orange parts, and erosion then dilation removed small noise dots. Haar detection found 1 face (the astronaut). `minNeighbors` 2 added a false face; 5 and 8 gave only the real one.
- **CNN:** 97.28%, against 95.45% for the ANN. The most common mistake was a 7 predicted as a 2.
- **RNN:** The GRU's RMSE was 2.31 °C against 2.49 °C for the naive baseline, about 7% better. The bonus LSTM scored 2.29 °C.
- **Transformers:** 9 of 10 answers were correct. Fill-mask got the capital of India wrong (pune, bangalore, mumbai), and the unanswerable question still received a confident score of 0.76.

## What I Would Build Next

- Train the CNN on all 60,000 MNIST images for more epochs, with data augmentation.
- Run each model with several seeds, since each was trained once and small gaps (GRU against LSTM) are not conclusive.
- Add humidity and pressure to the temperature model and forecast several days ahead.
- Replace the Haar cascade with a CNN face detector and test it on my own photos.
- Fine-tune a Transformer on question answering data that includes unanswerable questions, so it can say "no answer".
