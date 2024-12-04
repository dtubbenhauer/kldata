# Code and Erratum for *Big data approach to Kazhdan&#8211;Lusztig polynomials*

I collected a bit of Python code relevant for the paper *Big data approach to Kazhdan&#8211;Lusztig polynomials*
<a href="https://arxiv.org/abs/2412.01283">https://arxiv.org/abs/2412.01283</a> on this page. In 2024, the code runs in <a href="https://colab.google/">Google Colab</a>.

Here is are two links where to download the data associated to the project (all in .txt files): 

- <a href="http://www.normalesup.org/~lacabanne/kl/KL_polynomials_symmetric_group.html">Click</a>. This link is prefered.
- <a href="https://www.dropbox.com/scl/fo/uwh9nr9fg9sv2egmrph2z/h?rlkey=bmvxgpymlbd3g7p8x2jsm4b2p&e=1&dl=0">Click</a>. This link is a backup.

An Erratum for the paper *Big data approach to Kazhdan&#8211;Lusztig polynomials* can be found at the bottom of the page.

# Contact

If you find any errors in the paper *Big data approach to Kazhdan&#8211;Lusztig polynomials* **please email me**:

[dtubbenhauer@gmail.com](mailto:dtubbenhauer@gmail.com?subject=[GitHub]%web-reps)

Same goes for any errors related to this page.

# Limits of computation

Before we get started, let us say what was actually computed. We done by $S_n$ the symmetric group on $\{1,\dots,n\}$ of size $n!$. We write KL instead Kazhdan&#8211;Lusztig of for short. 
The KL polynomials take two permutations from $S_n$ as entries so there are $(n!)^2$ many. Fixing the first entry to be the identity permutation (as we did below), we are thus left with $n!$ KL polynomials.
In both cases, everything grows very fast in $n$, and we only look at the last case we computed.

- We have computed all KL polynomials for $n=7$. There are $25401600$ such polynomials and the output .txt file is 979.1 MB in size. The computational time was negligible.
- With the first permutation fixed, we have computed all KL polynomials for $n=11$. There are $39916800$ such polynomials and the output .txt file is about 600 MB in size. The computational time was around 60 days.
- We also computed one polynomial for $n=13$, and its list of coefficients is $$1,30,433,3994,26119,127617,481228,1431090,3404124,6529693,10129212,12681891,12724552,10099918,6218204,2889956,978297,229796,34889,3014,118,1.$$ The computation took around 60 days.

This makes us believe that, without extra ideas, this is probably the end of the computation. In the first case, the output file will be very large and potentially unmanageable. The second case, as one can expect some KL polynomials to take several hours to compute, but there are $479001600$ many KL polynomials.

# Google Colab notebook

The notebook is here:

<a href="https://colab.research.google.com/drive/1obJGlFBARVre8HukxnGrG4s13trZI-Yb?usp=sharing">https://colab.research.google.com/drive/1obJGlFBARVre8HukxnGrG4s13trZI-Yb?usp=sharing</a>

All the code in that notebook will run after uploading the .txt files. It is explained in the notebook what is needed and done, but all the plots from the paper can be found there.

# KL ball mapper

The KL ball mapper code is part of the above notebook, but it needs to run a long time. So we have precalculated some of them for the reader to explore, see here:

<a href="http://www.normalesup.org/~lacabanne/kl/3Dgraphs/">Click</a>

All of the files run in html. You will get something like:

<div style="text-align: center"><img src="https://github.com/dtubbenhauer/kldata/blob/main/ballmapper.png" width="800" height="800" style="border: 0px;" /></div><div style="text-align: center"><img src="https://github.com/dtubbenhauer/kldata/blob/main/ballmapper2.png" width="800" height="800" style="border: 0px;" /></div>

# High resolution pictures

One can change the resolution in the Google Colab notebook to create higher resolution plots such as:

<div style="text-align: center"><img src="https://github.com/dtubbenhauer/kldata/blob/main/highres.png" width="800" height="800" style="border: 0px;" /></div><div style="text-align: center"><img src="https://github.com/dtubbenhauer/kldata/blob/main/highres2.png" width="800" height="800" style="border: 0px;" /></div>

# Random polynomials

The paper also has some statistics associated to random polynomials. The file that we used is uploaded on this GitHub site.

The following Python code creates them; it can be run in Google Colab:

```
import random

# Parameters
num_polynomials = 293189  # Number of polynomials
degree_range = (1, 15)    # Degree range (inclusive)
coefficient_range = (0, 61582)  # Coefficient range (inclusive)
output_file = "polynomials.csv"  # Output file name

# Function to generate a single polynomial
def generate_polynomial():
    degree = random.randint(*degree_range)  # Random degree
    coefficients = [1] + [random.randint(*coefficient_range) for _ in range(degree)]  # Ensure x^0 coefficient is 1
    # Convert coefficients to a polynomial string
    polynomial = " + ".join(f"{coeff}*x^{i}" if i > 0 else "1" for i, coeff in enumerate(coefficients))
    return polynomial

# Generate all polynomials
polynomials = [generate_polynomial() for _ in range(num_polynomials)]

# Write to file
with open(output_file, "w") as f:
    f.write("Polynomial\n")  # Header
    f.writelines(f"{poly}\n" for poly in polynomials)

print(f"{num_polynomials} polynomials written to {output_file}.")
```

# Erratum

Empty so far.
