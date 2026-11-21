# Three finite prime-race scores determine a local Euler factor

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.24413207.svg)](https://doi.org/10.5281/zenodo.24413207)

This result is now maintained in [theta-host-split-inert-race](https://github.com/leecrossley/theta-host-split-inert-race/tree/main/results/theta-race-finite-euler-readout). This repository is archived and keeps its releases and DOI.

At every good odd rational prime $`p`$ of the 547/727 field, the signed prime-ideal counts at **three finite window starts** determine the entire local Euler denominator. The starts are $`(p-1)/4`$, $`p/4`$ and $`(p+1)/4`$. All nonzero terms in these measurements have ideal norm at most $`p`$. The reconstruction uses the prime modulo 16 and tolerates absolute error below $`(\log p)/p`$ in each unnormalised score. [Theorem and proof](PROOF.md)

For example, the three counts give trace $`-8`$ at 31 and trace $`8`$ at 47. Their denominators are $`(1+T)^8`$ and $`(1-T)^8`$. At 193 the trace is zero and the denominator is $`(1-T^2)^4`$. The proof also inverts a general signed integer-norm sequence, including the overlapping contributions at even norms. The five rational primes omitted from the race are treated separately using the character frame. [Three-score examples](evidence/finite-samples.tsv) · [Arithmetic scope](PROOF.md#which-euler-factor-is-recovered)

The finite-score calculation and an independent computation with eight primitive Dirichlet characters agree at all **78,498 rational primes through one million**. Of these, 78,495 are good odd primes measured by the three-score rule. Six local Lean lemmas check the kernel differences, inverse recurrence and rounding deductions. The proof uses the arithmetic trace identity and finite sums throughout. [Checks](evidence/check.txt) · [Lean deductions](FiniteReadout.lean) · [Prior work](PRIOR-WORK.md)

## Replay

In a Python 3.10+ virtual environment run

```sh
python -m pip install -r requirements.txt
python decode.py
python independent.py
python inverse.py
```

Run `python decode.py --all` to emit tab-separated rows in prime order. Each row gives $`p,f,s,d`$ for the denominator $`(1-sT^f)^d`$. The digest identifies the entire table. The five columns in the sample file are the prime, three integers representing raw scores scaled by $`10^{24}`$ and rounded to the nearest integer, and the recovered trace. [Factor table digest](evidence/factor-digest.txt) · [Source and enclosure calculation](decode.py)

On x86-64 Linux with Git, curl, tar and zstd, `bash verify-release.sh` verifies the manifest, repeats both arithmetic calculations and replays the Lean kernel. With Lean 4.33.1 on PATH and Mathlib at commit `0df444a360eaa60ab8c11dca51a86af692955474`, run `bash verify-release.sh /path/to/mathlib4`. [File hashes](SHA256SUMS)
