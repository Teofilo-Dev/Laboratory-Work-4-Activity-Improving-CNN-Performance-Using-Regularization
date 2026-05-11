# Laboratory-Work-4-Activity-Improving-CNN-Performance-Using-Regularization

# HERE IS MY LINK TO GOOGLE COLAB : https://colab.research.google.com/drive/1IKp3kKS_ZNFsDZg1_ShIr5kDURW0cRsa?usp=sharing

| Metric | Baseline Model | Improved Model |
| :--- | :---: | :---: |
| **Training Accuracy** | 99.77% | 85.45% |
| **Validation Accuracy** | 68.90% | 79.96% |
| **Precision** | 0.69 | 0.81 |
| **Recall** | 0.67 | 0.80 |
| **F1-score** | 0.68 | 0.80 |
| **AUC Score** | 0.85 | 0.95 |
| **Validation Loss** | 2.5624 | 0.8881 |


# GUIDE QUESTIONS :

A. Model Evaluation Analysis

1. What were the weakest-performing classes based on the confusion matrix?
  -The biggest problems were classes with high visual similarity, such as the white-petaled flowers Butterfly Ginger and Hairy Water Lily. These botanical            similarities often lead to “clusters” of miscategorization in the confusion matrix in a complex 20-class dataset. The improved model has reduced this, but the     basic problem in achieving 100% realism is the minute variations in flower architecture.

  
2. How did Precision, Recall, and F1-score vary across classes?
  -These metrics were much better balanced in the revised model compared to the baseline, which had unpredictable values. Classes with unique architecture shapes     such as Angel Wings did well, while classes with a lot of color diversity varied a bit more. The stabilization indicates that the model started to learn           repeating botanical patterns across the entire dataset rather than resorting to “lucky guesses.”
   

3. What does a low recall indicate in your model?
  -Poor recall means a high rate of “False Negatives”, or that the model is not detecting a plant when there is one. For example, if the recall is low, the           algorithm often confuses a Rafflesia with another red-colored species. This happens typically in the case that the training data for that class does not have      enough variation in illumination or angles to cover all real world situations .


4. How does AUC score reflect model performance compared to accuracy?
  -The AUC Score (0.95) indicates the overall ability of the model to distinguish between all 20 classes, while accuracy is only counting “correct” or “incorrect”    top predictions. It measures the probability that the model ranks a true class higher than a randomly chosen wrong class. A high AUC indicates that the model’s    second or third guess is frequently the right answer, even if its first guess is not.


B. Model Improvement

5. How did data augmentation affect validation accuracy?
  -Data augmentation significantly increased validation accuracy by artificially expanding the diversity of the training set. By randomly rotating, flipping, and     zooming into the plant images, the model was forced to learn the actual geometry and texture of the flowers rather than memorizing the orientation of specific     pixels. This made the model robust enough to achieve ~80% accuracy on new images it had never seen before.


6. Why is Batch Normalization important in CNNs?
  -By normalizing the inputs to each layer during training, batch normalization assisted in stabilizing the learning process. This allowed the model to employ a      higher learning rate without running the risk of inflating gradients and avoided the "internal covariate shift." As a result, the revised model successfully       trained deeper layers, resulting in a significantly reduced final validation loss of 0.88.


7. What role did Dropout play in improving your model?
  -Dropout (tuned to 0.4 and 0.5) was a powerful regularizer that randomly “muted” a fraction of neurons at each step of training. The Generalization Gap dropped     from 30% to 5% mainly because this prevented the network to over-rely on some pixels or to co-adapt neurons. It ensured high dependability by requiring the        model to learn many redundant properties for each plant species.


8. How did Early Stopping prevent overfitting?
  -Throughout the training process, Early Stopping served as an automated safety switch that tracked the validity loss. The system stopped training as soon as the    model started memorizing the training data instead of learning from it because it was employing a "patience" of 3. This prevented the performance decrease         observed in the baseline by ensuring that the final model retained the "best weights" from the top of its generalization capacity.


C. Performance Comparison

9. What improvements were observed after modifying the model?
  -The increase in validation accuracy from 68.90% to 79.96% was the biggest improvement. Furthermore, the validation loss decreased from a high 2.56 to a            constant 0.88, a reduction of more than half. These numerical improvements demonstrate the model's increased accuracy and confidence in its floral                 classifications.


10. Which enhancement contributed the most to performance improvement? Why?
  -Because Dropout and Data Augmentation directly addressed the extreme overfitting seen in Activity 1, their combination made the biggest contribution. Although     your baseline model achieved 99% training accuracy, it failed validation, suggesting that it had only "memorized" the photos. These two methods encouraged the     algorithm to acquire generalizable botanical traits by adding noise and variation.


11. Did the gap between training and validation accuracy decrease? Explain.
  -Yes, the generalization gap decreased dramatically from over 30% down to approximately 5%. In the baseline, the huge gap proved the model was overfitted and       unreliable for real-world use. The narrow 5% gap in the improved model indicates a "Healthy Model" that will perform consistently when deployed to identify        plants in the field.


D. Explainability (Grad-CAM Integration)


12. How did Grad-CAM help in understanding model predictions?
  -Grad-CAM highlighted the particular areas of the image that affected the final prediction, providing a "visual audit" of the CNN. It made it possible for us to    confirm that the model was making choices based on real plant components rather than background noise from soil or pots. Debugging whether the model is picking    up the right biological indicators depends on this transparency.


13. Did the improved model focus on more relevant regions? Provide evidence.
  -Yes, the improved model showed a much tighter focus on relevant botanical structures such as petals, pistils, and unique leaf patterns. For example, in your       Grad-CAM overlays for the Bagawak Morado, the "hot" regions were centered directly on the vibrant red floral structures. This provides visual evidence that the    added layers and regularization helped the model ignore background distractions.


14. Why is explainability important in real-world AI applications?
  -Building trust between the end-user and the AI system requires explainability, or XAI. A user must be aware that the AI is identifying a plant in a botanical      or agricultural context using scientific characteristics rather than accidental lighting or backdrop patterns. For professional scientific application, the        system is safer and more dependable when the model considers the "right" things.

