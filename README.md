# Ml
Ml prototype for BB2

TODO add bias grad
dW2 = np.dot(A1.T, dZ2) / m
db2 = np.sum(dZ2, axis=0, keepdims=True) / m