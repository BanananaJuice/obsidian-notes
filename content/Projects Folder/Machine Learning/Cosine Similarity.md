## Summary

Cosine similarity is a statistical measure to calculate the similarity between two discrete values


-------------------------------------------------------------------
## Related Sections/Pre-Reading

N/A

-------------------------------------------------------------------
## Content

Let’s say you have two documents with the following word counts (vectors):

- **Document A**: [3 apples, 0 oranges, 2 bananas]
- **Document B**: [1 apple, 1 orange, 1 banana]

We can think of each document as a point in 3D space (the dimensions are apples, oranges, and bananas).

- Document A is at point (3, 0, 2) because it has 3 apples, 0 oranges, and 2 bananas.
- Document B is at point (1, 1, 1) because it has 1 apple, 1 orange, and 1 banana.

Now, to find how similar these documents are, cosine similarity calculates the angle between their directions. If they point in the same direction, they’re similar. If they point in different directions, they’re not.

Without going into math details, the cosine similarity for these two documents will be a number between 0 and 1:

- **1** means they’re pointing in exactly the same direction (very similar).
- **0** means they’re not related at all.

In this case, the cosine similarity would be a value closer to 1, meaning the documents are fairly similar because both mention apples and bananas (though Document B also mentions oranges).

### Example
Let's calculate the cosine similarity for **Document A** and **Document B** step by step using their word counts as vectors.

### Step 1: Represent the Documents as Vectors

We have the word counts for apples, oranges, and bananas:

- **Document A (Vector A)**: [3, 0, 2]  
    (3 apples, 0 oranges, 2 bananas)
    
- **Document B (Vector B)**: [1, 1, 1]  
    (1 apple, 1 orange, 1 banana)
    

### Step 2: Apply the Cosine Similarity Formula

The formula for cosine similarity is:

$$

\text{Cosine Similarity} = \frac{A \cdot B}{\|A\| \|B\|}

$$

Where:

- A.B is the **dot product** of the two vectors.
- ∥A∥B∥ are the **magnitudes** (lengths) of the vectors.

#### Step 3: Calculate the Dot Product A.B

The dot product is calculated by multiplying the corresponding elements of the two vectors and then summing them up:

$$

A \cdot B = (3 \times 1) + (0 \times 1) + (2 \times 1)
$$
$$
A \cdot B = 3 + 0 + 2 = 5


$$

#### Step 4: Calculate the Magnitude of Each Vector

The magnitude of a vector ∥A∥∥ is calculated using this formula:

$$

\|A\| = \sqrt{(a_1^2 + a_2^2 + a_3^2)}


$$


For **Vector A [3, 0, 2]**:

$$
\|A\| = \sqrt{(3^2 + 0^2 + 2^2)} = \sqrt{(9 + 0 + 4)} = \sqrt{13} \approx 3.605


$$

For **Vector B [1, 1, 1]**:

$$

\|B\| = \sqrt{(1^2 + 1^2 + 1^2)} = \sqrt{(1 + 1 + 1)} = \sqrt{3} \approx 1.732


$$

#### Step 5: Calculate the Cosine Similarity

Now, plug the dot product and magnitudes into the formula:

$$


\text{Cosine Similarity} = \frac{5}{(3.605 \times 1.732)}
$$
$$


\text{Cosine Similarity} = \frac{5}{6.245} \approx 0.801


$$