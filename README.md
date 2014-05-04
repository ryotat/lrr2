# Matlab code for "Logistic Regression for Single Trial EEG Classification" (NIPS 2006)

## Instructions
Please unzip the attachment. The main solver routine is called `lrr2.m`
You should preprocess each epoch into convariance matrix and apply
whitening before calling `lrr2`. Basically `lrr2` can be called as
```matlab
   [W, bias, stat] = lrr2(Xtr, Ytr, lambda);
```
where Xtr is CxCxn (C: #channels, n: #epochs), and Ytr is nx1 (vector of
-1 or +1), and lambda is the regularization constant. W is Cx2 coefficient
matrix and bias is the bias term.

The program uses the MATLAB optimization toolbox (`fminunc`).  If you
don't have the toolbox, you can also choose an internal L-BFGS solver by
specifying the 'solver' option as
```matlab
   [W, bias, stat] = lrr2(Xtr, Ytr, lambda, 'solver','lbfgs');
```
However, since L-BFGS assumes that the Hessian is possitive
definite, the result is not as stable as the optimization toolbox.
Note that the objective function is not convex.

To see how the data should be preprocessed and everything, please
run the script `s_bcicompIIIiva.m`. Please also download the BCI
Competition III dataset iv to run the script.
http://www.bbci.de/competition/iii/index.html#data_set_iva

## Notes
 * Feedback and comments are welcome. Email: tomioka [AT] ttic [DOT] edu
 * This software is provided as is and although I will try to help you to make the best use out of it, I will not take any leagal responsibility about the consequence.
 * My limited memory BFGS routine is based on Jorge Nocedal's [work](http://www.eecs.northwestern.edu/~nocedal/lbfgs.html) and Naoaki Okazaki's [liblbfgs](http://www.chokkan.org/software/liblbfgs/).
