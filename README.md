# chess_AI
Development of CHESS AI using Tensorflow and MiniMax Tree 

The Download link for the chess_data is avaliable in kaggle and the link is here 
[1]: kaggle kernels output abhishekcody/own-chess-ai -p /path/to/dest

# Chess AI Idea History
# Shannon’s Approach For Computational chess![image](https://user-images.githubusercontent.com/97011879/171464105-22498692-8a45-4248-b7e1-31d9c9d02bf8.png)

- In1949 Shannon published a ground breaking paper on computer chess entitled Programming a Computer for Playing Chess
- He suggested and categorized two types of search :
   -Type A - A brute Force search looking at every variation to a given depth
   -Type B - A selective search looking at "important" branches only Without the sense of alpha-beta, and inspired by the experiments of Adriaan de Groot
- Shannon and early programmers has favoured the Type B strategy.  As Type B searches use some type of static heuristics in order to only look at branches that look important  with some risk to oversee some serious tactics not covered by the plausible move selector. 
- Type B was most popular until the 1970's, when Type A programs had enough processing power and more efficient brute force algorithms to become stronger. Today most programs are closer to Type A, but have some characteristics of a Type B.
![image](https://user-images.githubusercontent.com/97011879/171464173-19e3d110-b2b3-4480-9e36-e050b6202c8c.png)

# Approach of Our Chess AI model![image](https://user-images.githubusercontent.com/97011879/171464612-07834cde-5b40-40f6-a354-a5a1b149d27c.png)
- Selection of language and importing necessary library
  - Python3 is selected.
  - For Deep learning TensorFlow, keras was imported for making CNN model and python-chess library is imported for defining the chess board and chess piece.
- Chess Board making and evaluation
  - A function is defined for representing chess board and pieces are present in random position.  
  - Evaluation of random chess piece position is done using stockfish engine which tells us which colour is winning and also gives the score.
- Creation of computer understandable chess Board
  - Creation of matrix of 14 ×8×8 as the chess board is 8×8 and 14 represent the 7 different pieces.
  - A Function is defined which convert the chess square into index position in the matrix.
  - A function is defined which add piece view in the matrix and also find the valid moves and also the network find which piece is attack and also find what are the attacking moves.
![image](https://user-images.githubusercontent.com/97011879/171464627-91ee9702-2b23-4c0e-b55d-a5ba1c2968b5.png)

- Creation of CNN model
  - function is define for the model on the basis of the parameter of depth. 
  - Its a simple Convolutional layer with a flatten layer proceeding it. It contains a ‘same’ padding parameter as we do not want to change the overall dimensions of the input during the flow.
  - Skip connections (residual network) can also be used  for improve the model for deeper connections. [NOT IMPLEMENTED].
- Training of CNN Model
  - The model is trained using the dataset of player in lichess.org and the dataset is in the form od npz format and the dataset is then divide into X_train and Y_train format.
  - Defining of MINIMAX tree is defined for find the possible best move in a given depth .
- Playing with AI
  - Game is played between the generated model and stockfish.
  - Game is played between the generated model and human (ME) where the input is given in the form of chess coordinate.
![image](https://user-images.githubusercontent.com/97011879/171464817-601075b6-552a-45da-807e-7be8393d1702.png)

# MiniMax Algorithm
- Search tree backtracking algorithm, minimize possible loss (expect opponent to make best possible move)
- Because chess is a zero-sum game, the minimax algorithm takes use of that. Minimizing your opponent's chances of winning is the same as increasing your own chances of winning.
- Each turn can be seen as a player making a move to maximize the evaluation function while the other tries to minimize it. Which is incredibly slow and makes it impractical.
- Minimax Algorithm moves in depth-first fashion down the tree until it reaches a terminal node (i.e. someone wins the game) or a pre-determined depth limit


![image](https://user-images.githubusercontent.com/97011879/171465081-30794b16-55fe-49a6-814d-97485a271394.png)

# Alpha and Beta algorithm	![image](https://user-images.githubusercontent.com/97011879/171465476-acad767e-f3bb-4fe8-b5ce-c46cfb778623.png)
- The Alpha-Beta algorithm (Alpha-Beta Pruning, Alpha-Beta Heuristic) is a significant enhancement to the minimax search algorithm that eliminates the need to search large portions of the game tree applying a branch-and-bound technique.
- Alpha-beta pruning speeds up minimax by skipping the “irrelevant” nodes of a search tree. This can be accomplished by adding extra data to each node, an “alpha” and a “beta” value, which represent the worst outcome for each player from that node
![image](https://user-images.githubusercontent.com/97011879/171465508-161d829f-9f28-42e4-ae08-d76c9d2d66ec.png)

![image](https://user-images.githubusercontent.com/97011879/171465554-f4971a91-ac6b-4b85-bb4a-0a3fd9ed8353.png)

