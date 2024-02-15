# Sentiment-Analysis-Subtheme
 The goal is to devise a method that, when given a sample, can discern sub-themes and their associated sentiments.

 <center>
<img src="https://i.ibb.co/yRJJ5wH/Screenshot-2020-10-03-042959.jpg" alt="Screenshot-2020-10-03-042959" border="0">
</center>

## Approach
### Exploratory Data Analysis
Through Exploratory Data Analysis (EDA), I discovered approximately 10,000 data points with roughly 90 unique labels, yet many of these labels exhibit noise and occur infrequently. Following preprocessing and undersampling of the more prevalent labels, the dataset has been refined to 23 unique labels and approximately 6,000 data points.

### My Approach

I approached this challenge as a multi-label classification task and employed pre-trained BERT models, fine-tuning them for training. Opting for pre-trained BERT models allowed me to harness the power of language models, which is particularly advantageous given the predominantly review-based nature of the data. Additionally, the implementation was streamlined, and I utilized Binary Cross Entropy with Logits as the chosen loss function.


I experimented with both bert-base-uncased and bert-large-uncased pre-trained models for training the data. While bert-large-uncased exhibited slightly better performance, I opted to stick with bert-base-uncased for this project due to its smaller size. You can access the trained model here. (https://drive.google.com/file/d/1kcs0WctkGAqLrzSI1QhsnmK05AG5gopd/view?usp=sharing).

### Performance Metrics 
**Micro F1 Score:**
Compute metrics on a global scale by tallying the overall true positives, false negatives, and false positives. This metric is particularly valuable in scenarios with class imbalance.


**Macro F1 Score:**
Compute metrics independently for each label and determine their unweighted average. This approach does not consider label imbalances.


## Results 
After 5 Epochs model started overfitting. More Details in Model-Analysis 
<table class="tg">
<thead>
  <tr>
    <th class="tg-0pky"><span style="font-weight:bold">Metric</span></th>
    <th class="tg-0pky"><span style="font-weight:bold">Training</span></th>
    <th class="tg-0pky"><span style="font-weight:bold">Validation</span></th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0pky"><span style="font-weight:bold">BCE Loss</span></td>
    <td class="tg-0pky">0.019</td>
    <td class="tg-0pky">0.025</td>
  </tr>
  <tr>
    <td class="tg-0pky"><span style="font-weight:bold">F1-Micro-Score</span></td>
    <td class="tg-0pky">0.821</td>
    <td class="tg-0pky">0.737</td>
  </tr>
  <tr>
    <td class="tg-0pky"><span style="font-weight:bold">F1-Macro-Score</span></td>
    <td class="tg-0pky">0.618</td>
    <td class="tg-0pky">0.536</td>
  </tr>
  <tr>
    <td class="tg-0pky"><span style="font-weight:bold">Hamming Loss</span></td>
    <td class="tg-0pky">0.031</td>
    <td class="tg-0pky">0.046</td>
  </tr>
</tbody>
</table>

## Shortcomings and Improvements 
1. During Exploratory Data Analysis (EDA), labels with a frequency less than 100 were consolidated into a single label based on sentiment. However, to address this limitation of ignoring certain labels, an enhancement can be achieved by oversampling those labels through combinations of co-occurring labels.

2. Exploring various layer configurations on top of pre-trained BERT models presents an opportunity for further improving results.

3. Conducting Hyper-Parameter tuning, specifically for Batch Sizes and Learning Rate, has the potential to enhance overall performance.

4. While Binary Cross Entropy (BCE) Loss was utilized, exploring alternative loss functions could potentially yield improved results.
