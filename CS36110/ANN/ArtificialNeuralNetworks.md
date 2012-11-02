#Artificial Neural Networks

##Single Neuron to compute AND
![Neuron](https://github.com/JustSomeBrosDoingScience/SCIENCE/raw/ANN/CS36110/ANN/ann.png)

*Why these numbers? - No reason in particular, they are simply in proportion (e.g. you can use -1.5, 1, and 1 for the weights and it will work the same.*

Blue units = Input layer - the features of a single example in the training set X

Red numbers = Theta - the weights of the input to the next layer. Assume that the network has finished training and these vlues of Theta are the results.

###Truth table with threshold activation function

g(Theta0 * X0   +   Theta1 * X1  +  Theta2 * X2)

If g(z) is over the 'threshold' (0 in this case) then h(x) = 1; 0 otherwise.

<table>
  <tr>
    <th>X1</th><th>X2</th><th>g(z)</th><th>h(x)</th>
  </tr>
  <tr>
    <td>0</td><td>0</td><td>g((-30 * 1)   +   (20 * 0)  +  (20 * 0)) = -30</td><td>0</td>
  </tr>
  <tr>
    <td>0</td><td>1</td><td>g((-30 * 1)   +   (20 * 0)  +  (20 * 1)) = -10</td><td>0</td>
  </tr>
  <tr>
    <td>1</td><td>0</td><td>g((-30 * 1)   +   (20 * 1)  +  (20 * 0)) = -10</td><td>0</td>
  </tr>
  <tr>
    <td>1</td><td>1</td><td>g((-30 * 1)   +   (20 * 1)  +  (20 * 1)) = 30</td><td>1</td>
  </tr>
</table>