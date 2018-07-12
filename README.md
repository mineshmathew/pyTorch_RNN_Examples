# pytorch RNN Examples
Few sequence learning problems using RNNs are introduced here. Maintained mostly from a learning persepctive.<br>
If you are looking for reusable, optimal solutions this repo need not suit your requirements<br>
I will try to add more explanatory figures, and write-up in the future 


## Table of Contents
- Seq2One
  * <a href='#Memorize Kth Integer in a Sequence'> Memorize Kth Integer in a Sequence </a>
- Se2Seq with alignment
  * <a href='#Binary Strings Addition'> Binary Strings Addition </a>
- Se2Seq without alignment
  * <a href='#OCR using BRNNs and CRNNs'> OCR using RNN and a CRNN </a>
  
  
### Memorize Kth Integer in a Sequence
The problem here is to memorize kth digit in a sequence of digits of varibale length. Say if the sequence is 9,7,0,5,6 and k=3, network should output 0. This is a sequence to one problem where input digits are represented suing one hot vectors of length=10 (since there are 10 digits)

### Binary Strings Addition
This problem introduces a simple sequence to sequence learning example where the task is to make an RNN learn the binary addition. Problem is modelled as a seq2seq, where input and output sequences are aligned.<br>

Corresponding bits from the input strings forms a 2 - element input vector at each time- step and the target  or desired bit is the corresponding bit from the output binary string. Prior to this we make sure that input sequences are padded with a 'zero' on the left if the output string has one extra bit. The sequence is processed from the Least significant bit (LSB) to the Most Significant Bit(MSB) since thats how the addition is done. <br>

Network has 2 input nodes, 10 or 20 hidden LSTM nodes  and a single output node followed by a Sigmoid activation. MSE loss is computed at each each time step between the output activation at the output node and the desired bit at that time step. At the last time step, sum of the losses is calcuated and then the error is backropagated.




### OCR using RNN and CRNN
OCR is probably one of the easiest vision problems to introduced the utility of RNNs in sequence learning. Here we introduce seq2seq learning, without input and output sequence alignment. 'Without alignment' means that, you dont have a  corresponding target at each time step and the input and output lengths may vary. All you know is that you have an input sequence of features and you need to map it to an output sequence of class labels.<br>

Here OCR is modelled as a seq2seq learning, where a sequence of image features are extracted from the input word or line image and the output is a sequence of characters or Unicodes.<br>

[CTC](http://www.cs.toronto.edu/~graves/icml_2006.pdf) loss is employed to cacluate the cost here.

This example also showcases two variants of the soltuion:-
- one using raw pixel values as input features for the RNN
- and in the second case a convolutional stack is added at the head of the network to extract more robust features from the input image. Then a sequence of convolutional features are supplied to the RNN. This model is generally referred by the  name -CRNN (The first paper which introduced such a model for text recognition is this [one](https://arxiv.org/abs/1507.05717)
