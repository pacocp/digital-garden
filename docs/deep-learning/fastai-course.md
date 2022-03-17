# Notes on the Fastai course

## Lesson 0

- "I always think that my machine learning code is wrong".
- Always start with a simple baseline and then build up from this.

## Lesson 1

- David Perkins: "In order to learn something is better to play a full-game and then learn the basis:
    1. Play the whole game.
    2. Make the game worth playing.
    3. Work on the hard parts."
- SGD just do a lot of multiplication and addition.
- Take into account how the model interacts with the environment.
- How the model is used need to be clear.
- The validation and tests sets need to be a clear representation of the data that the model will encounter in the future.

## Lesson 2

- The metric is a fuction that measures the quality of the model's prediction.
- The metric is the thing we care about: the loss might change a little but without affecting the metric.
- Sometimes the the loss value in validation will go up but the metric will improve.
- Catastrophic forgetting: the model get worse at the original task by putting new samples of the new task.
- How we might decide if there is a relationship in the data?

    ```
        Pick a null hypothesis -> Gather data of independent and dependent variables -> What % of the time would we see that relationship by chane?
    ```
- A small p-value just says that maybe the correlation didn't happend by chance.
- For practical importance you need to look at the values.

## Lesson 3

- Squared images are better to have homogeneous information in each batch.
- The squish method for transforming images is the most efficient.
- A random resize crop is the most common approach since it can helps to avoid overfitting
- voila for Jupyter Notebooks -> displays only the markdown and the widgets.
- When doing inference, CPU is usually more efficient and cheap.
- You need to look at your dara carefully in order to not include bias.
- out of domain data -> data that is in some way different to the data you used to train the model.
- domain shift -> data that change over time.
- One of the most difficult problems when  deploying ML models are feedback loops.
- Always think about what would happen of the model worked really well.
- Pytorch tensors can be used within the GPU.
- A baseline model is the simplest model that can be better than a random model.
- Always start with a reasonable baseline.
- Broadcasting -> apply the same operation in a given dimension. But in pytorch it doesn not allocate new memory.
- The gradient is the slope of the function.
- When we change the weights we do it as:
    ```
    w -= gradient(w) * lr
    ```
    - we are substracting since we want to minimize the loss
- we cannot use a metric as the loss, since usually the gradient of a metric is zero.

## Lesson 4

- -1 in Pytorch means "as many as there are in the data".
- *unsqueeze* gives an additional dimension.
- simple way to create a dataset in pytorch:
  ```python
  dset = list(zip(train_x, train_y))
  ```
- The weights and the biases are the parameters.
- In Pytorch, @ iis the matrix multiplication operation:
  ```python
  batch@weights + bias
  ```
- Accuracy -> not good as a loss function!
- For computing the loss in a binary problem:

  ```python
    torch.where(trgt == 1, 1-preds, preds)
  ```
- In order to prevent that all numbers are going to be 0 and 1, we use the
  sigmoid function:

  ```python
  sigmoid = 1 / (1 + exp(-x))
  ```
- With loss.backward() the loss is added to what was previously stores.
- Simple neural net:

  ```python
  def simple_net(xb):
    res = xb@w1+b1
    res = res.max(tensor(0.0)) # non-linearity
    res = res@w2+b2
    return res
  ```
- By putting a non-linearity you obtain an universal approximator.
- The initialization of the weights is really important.
- **activations**: numbers we are computing ; **parameters**: numbers that we are
  learning.
- Regular expressions are really useful, learn them!
- softmax is really useful since the exponent grows really fast, so it would
  always choose a class.
- logarithms are really useful in DL since:

  ```
  log(a*b) = log(a) + log(b)
  ```
