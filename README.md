# neural_style_transfer

After learning about it in a deep learning course, I wanted to experiment with neural style transfer, which uses a model to transfer the style of an image to another one. The styles are captured by an already trained neural netwrok like VGG19, and then the generated image is optimized to have a similar style to the reference image while retaining the features of the base image by using gradient descent. I used the sample code from the [Keras website](https://keras.io/examples/generative/neural_style_transfer/) to see what I can do with it. 

After playing around with it for a while, I felt like stepping things up a bit. I wanted to have two separate images transfer their styles to a base image simultaneously. I basically wanted to have Van Gogh and Picasso collaborate on editing one of Dali's paintings. I tried three approaches to accomplish this:

  1- I made the model calculate the style loss for each style image separately and added both to the total loss on every iteration.  
  2- I took element-wise averages of the feature matrices for each style image on every iteration of feature extraction before calculating the style loss.  
  3- I took element-wise averages of the Gram matrices, which are used to calculate style loss, and instead used these averages to calculate the style loss.  

Out of the three approaches, in my opinion visually the third one worked best. As Gram matrices capture the correlation between the channel activations, they almost represent the style of the image mathematically, and thus averaging the correleations helped the model apply both styles in a balanced way.

Here are three example images generated with this approach:

[generated_image_1](https://github.com/emrealtinok/neural_style_transfer/blob/main/generated_image_1.png): Monet and Picasso styles applied on a Dali  
[generated_image_2](https://github.com/emrealtinok/neural_style_transfer/blob/main/generated_image_2.png): Matisse and Van Gogh styles applied on another Dali  
[generated_image_3](https://github.com/emrealtinok/neural_style_transfer/blob/main/generated_image_3.png): Picasso and Van Gogh styles appplied on another Dali  
