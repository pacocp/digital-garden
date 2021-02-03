# Variational Autoencoders

- Variational autoencoders follow the same principal as autoencoders.
- However, a constraint is added th the encoder network, that forces it to
  generate latent vectors that roughly follow a unit gaussian distribution.
- Therefore, the loss is the recostruction error plus a latent loss, which is the KL divergence that measures how closely the latent variables match a unit gaussian.

```
generation_loss = mean(square(generated_image - real_image))  
latent_loss = KL_Divergence(latent_variable, unit_gaussian)  
loss = generation_loss + latent_loss  
```
