## Variational autoencoder (VAE) for learning latent structure in facial data (Debiasing approach)
<h3 align="center">
<p>Traditional Architecture of VAE</p>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20200710000625/variational-660x370.jpg" width="500"> 
</h3>
<br>
The general idea behind the VAE architecture to build a model, termed a debiasing variational autoencoder DB-VAE to remove unknown biases present within the training idea. We'll train our DB-VAE model on the facial detection task, run the debiasing operation during training, evaluate on the PPB dataset, and compare its accuracy to our original, biased CNN model.
<br>
<img width="1109" alt="68747470733a2f2f7261772e67697468756275736572636f6e74656e742e636f6d2f61616d696e692f696e74726f746f646565706c6561726e696e672f323031392f6c6162322f696d672f44422d5641452e706e67" src="https://user-images.githubusercontent.com/18554133/176991506-e9e4eccf-c45b-424a-9599-557fe6cede6d.png">
<h3 align="center">
<p>DB-VAE Architecture</p>
</h3>
<p>
Recall that we want to apply our DB-VAE to a supervised classification problem -- the facial detection task. Importantly, note how the encoder portion in the DB-VAE architecture also outputs a single supervised variable Zo
, corresponding to the class prediction -- face or not face. Usually, VAEs are not trained to output any supervised variables (such as a class prediction)! This is another key distinction between the DB-VAE and a traditional VAE.
<br>
Keep in mind that we only want to learn the latent representation of faces, as that's what we're ultimately debiasing against, even though we are training a model on a binary classification problem. We'll need to ensure that, for faces, our DB-VAE model both learns a representation of the unsupervised latent variables, captured by the distribution Qo (z/x) and outputs a supervised class prediction Zo but that, for negative examples, it only outputs a class prediction Zo

For face images, our loss function will have two components:

                                       1. VAE loss: consists of the latent loss and the reconstruction loss.
                                       2. Classification loss: standard cross-entropy loss for a binary classification problem.

</p>
<h3 align="center">
	<img src="https://miro.medium.com/max/1328/0*XEZTAN4dbZSEhY53.gif" width="500">
</h3> 
</p>
