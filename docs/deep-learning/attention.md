# Attention

- You need to recall back longer than what RNNs are capable of.

- Dot production attention: 
  - A(Q,K,V) = softmax(QK^T)V
 
- In attention you want to find the most similar key (K) to the query (Q).

- You need to add some positional information. This is fixed with Multi-Head
  attention:
  - Each head uses different linear transformations.
  - Different heads can learn different relationships.

```python

# PSEUDOCODE

def attention(self, x_in:List[Tensor]):
  # For every layer transform previous layer's out
  for i in range(self.sequence_length):
    query[i] = self.Q * x_in[i]
    key[i] = self.K * x_in[i]
    value[o] = self.V * x_in[i]
  
  # compute output values, one at a time
  for i in range(self.sequence_length):
    this_query = query[i]
    # how relevant is this input to this output?
    for j in range(self.sequence_length):
      relevance[j] = this_query * key[j]
    
    # normalize scores to sum 1
    relevance = scaled_softmax(relevance)
  
    # compute weighted sum of oupits
    out[i]
  
    for j in range(self.sequence_length):
      out[i] = relevance[j] * value[j]

  return out   

```
