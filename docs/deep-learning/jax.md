# Jax

- [Jax](https://github.com/google/jax)  is a library developed by a team from Deepmind and Google Brain.
- Jit compiles code using xla technology in order to speed up our code for our
  device (CPU or GPU). 
- This helps a lot for vectorazing and mapping.
- An example of vmap:
  
  ```python
    import jax.numpy as jnp
    import numpy as np
    from jax import vmap

    def f(x):
      return jpn.array([jnp.min(x), jnp.max(x)])
  
    bx = np.arange(24).reshape(4, 2, 3)
    
    y = f(bx) # doesn't take into account batch size
    
    v_f = vmap(f)
    w = v_f(bx) # vf in: (BT, 2, 3) out: (B, 2)

  ```

## Resources

- [From jax fundamentals to running on a tpu pod slice](http://matpalm.com/blog/ymxb_pod_slice/) by Mat Kelcey.
 
