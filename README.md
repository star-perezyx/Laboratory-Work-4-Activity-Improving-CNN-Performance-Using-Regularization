# Laboratory-Work-4-Activity-Improving-CNN-Performance-Using-Regularization

# Google Colab Link:<a href="https://colab.research.google.com/drive/1GiWm9DsWHaCJaXEEUpIuWj-qEpcv3TCH?usp=sharing">CLICK HERE</a>!

<table style="width: 375.156px;">
<tbody>
<tr>
<td style="width: 142px;">Metric&nbsp;</td>
<td style="width: 107px;">&nbsp;Baseline Model</td>
<td style="width: 107.156px;">Improved Model&nbsp;</td>
</tr>
<tr>
<td style="width: 142px;">&nbsp;Training Accuracy</td>
<td style="width: 107px;">&nbsp;0.81</td>
<td style="width: 107.156px;">0.8984</td>
</tr>
<tr>
<td style="width: 142px;">&nbsp;Validation Accuracy</td>
<td style="width: 107px;">&nbsp;0.82</td>
<td style="width: 107.156px;">0.9144</td>
</tr>
<tr>
<td style="width: 142px;">Precision</td>
<td style="width: 107px;">&nbsp;0.86</td>
<td style="width: 107.156px;">0.86</td>
</tr>
<tr>
<td style="width: 142px;">&nbsp;Recall</td>
<td style="width: 107px;">&nbsp;0.82</td>
<td style="width: 107.156px;">&nbsp;0.82</td>
</tr>
<tr>
<td style="width: 142px;">F1-score</td>
<td style="width: 107px;">&nbsp;0.82</td>
<td style="width: 107.156px;">&nbsp;0.82</td>
</tr>
<tr>
<td style="width: 142px;">AUC Score</td>
<td style="width: 107px;">0.9929</td>
<td style="width: 107.156px;">0.9929</td>
</tr>
</tbody>
</table>
<!-- DivTable.com -->

GUIDE QUESTIONS (Student Explanation & Reflection)<br>
# A. Model Evaluation Analysis<br>
# 1. What were the weakest-performing classes based on the confusion matrix?
Ans: Based on the Classification Report, 'goldenrod flower' and 'yarrow' were among the weakest in precision (both 0.52), while 'artichoke flower' and 'hawthorn flower' had notably low recall (0.50 and 0.45 respectively).

# 2. How did Precision, Recall, and F1-score vary across classes?
Ans: There is high variance. Classes like 'blue lotus' and 'chamomile' are near-perfect (F1 > 0.90), while others struggle below 0.70. This suggests some flowers have much more distinct features than others.

# 3. What does a low recall indicate in your model?
Ans: A low recall (like 0.45 for Hawthorn) indicates the model is frequently missing that flower. It often thinks a Hawthorn is something else (high False Negatives).

# 4. How does AUC score reflect model performance compared to accuracy?
Ans: While the accuracy is 82%, the AUC is a very high 0.9929. This means the model is excellent at ranking the correct class higher than others, even if its final 'hard' decision is sometimes wrong.

# B. Model Improvement<br>
# 5. How did data augmentation affect validation accuracy?
Ans: It helped stabilize the model. In the 'Improved Model' training, the validation accuracy reached a peak of 91.44%, showing that teaching the model to see flipped/rotated versions makes it more robust.

# 6. Why is Batch Normalization important in CNNs?
Ans: This was included in the new architecture to normalize the activations of each layer, which allowed for faster training and helped mitigate the 'vanishing gradient' problem.

# 7. What role did Dropout play in improving your model?
Ans: I used Dropout (up to 0.5) to randomly ignore neurons during training. This prevents the model from relying too heavily on specific pixels, forcing it to learn more general patterns.

# 8. How did Early Stopping prevent overfitting?
Ans: Early Stopping terminated the training at Epoch 12. Since the best weights were restored from Epoch 9 (val_loss 0.2321), it prevented the model from continuing to learn noise in the training set which would have increased the error on new data.

# C. Performance Comparison<br>
# 9. What improvements were observed after modifying the model?
Ans: The 'improved' model reached a peak validation accuracy of 91.44%, which is significantly higher than the baseline's 82%.

# 10. Which enhancement contributed the most to performance improvement? Why?
Ans: Likely the Data Augmentation and Dropout combination. CNNs on small flower datasets tend to overfit quickly; adding these forced the model to learn shapes rather than specific image orientations.

# 11. Did the gap between training and validation accuracy decrease? Explain.
Ans: The gap decreased significantly during the middle epochs (Epoch 9: ~89% train vs ~91% val), indicating that the model was generalizing very well before it started to diverge slightly near Epoch 12.

# D. Explainability (Grad-CAM Integration<br>
# 12. How did Grad-CAM help in understanding model predictions?
Ans: It allowed me to visualize a heatmap over the image. In the Grad-CAM Overlay, the 'hot' areas (red) show exactly which pixels influenced the model's decision.

# 13. Did the improved model focus on more relevant regions? Provide evidence.
Ans: The heatmap shows the model focusing on the central structure of the flower rather than background leaves, which is evidence of a 'smarter' model.

# 14. Why is explainability important in real-world AI applications?
Ans: In real-world AI (like medicine or agriculture), it’s not enough to be right; we need to know why. If a model identifies a flower based on a watermark or a specific pot rather than the petals, it will fail in the wild.
