# Tiny Toy Network README

This document describes the purpose and usage of the Tiny Toy Network.

## What it is
`index.html` is a standalone interactive visualization for a tiny fully
connected network with a sigmoid activation between layers. The goal is to have a network small enough where I can apply backpropagation by hand, thus helping with memory retention fo the topic.

The network has:

- Weights and biases for Layer 1 and Layer 2
- A computational graph diagram
- Forward-pass values (`x`, `z1`, `h`, `z2`)
- Per-sample gradients (`dE/dx`, `dE/dW`, `dE/db`, `dE/dz1`, `dE/dh`)

## How to use
- Open `index.html` in a browser.
- Click "Randomize weights/biases" to generate new values.
- Click "Compute gradients (per sample)" to fill the gradient table.
- Use the column toggles to hide/show specific gradient columns.

## Math conventions
- Forward pass uses row vectors: `z2 = h @ W2 + b2`
- Loss uses mean-squared error per sample: `E = 0.5 * sum((z2 - y)^2)`
- Backprop uses:
  - `dE/dz2 = z2 - y`
  - `dE/dW2 = h^T * dE/dz2`
  - `dE/dh = dE/dz2 @ W2^T`
  - `dE/dz1 = dE/dh * sigmoid'(z1)`
  - `dE/dW1 = x^T * dE/dz1`
  - `dE/dx = dE/dz1 @ W1^T`
