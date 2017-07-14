# pytorch RNN Examples
Few sequence learning problems using RNNs are introduced here. Maintained mostly from a learning persepctive.<br>
If you are looking for reusable, optimal solutions this repo need not suit your requirements<br>
I will try to add more explanatory figures, and write-up in the future 


### Table of Contents
- <a href='#Binary Strings Addition'> Binary Strings Addition </a>
- <a href='#OCR using BRNNs and CRNNs'> OCR using RNN and a CRNN </a>


## Binary Strings Addition
This problem introduces a simple sequence to sequence learning example where the task is to make an RNN learn the binary addition. Problem is modelled as a seq2seq, where input and output sequences are aligned.<br>

Corresponding bits from the input strings forms a 2 - element input vector at each time- step and the target  or desired bit is the corresponding bit from the output binary string. Prior to this we make sure that input sequences are padded with a 'zero' on the left if the output string has one extra bit. The sequence is processed from the Least significant bit (LSB) to the Most Significant Bit(MSB) since thats how the addition is done. <br>

Network has 2 input nodes, 10 or 20 hidden LSTM nodes  and a single output node followed by a Sigmoid activation. MSE loss is computed at each each time step between the output activation at the output node and the desired bit at that time step. At the last time step, sum of the losses is calcuated and then the error is backropagated.




## OCR using RNN and CRNN
