# Revised Codes for Generalized Bent Functions

This repository contains the PARI/GP programs and exact computational
certificates accompanying a revised manuscript by Shi Ying and Yingpu Deng
on nonexistence results for generalized bent functions and extensions of the
element partition method.

The files are grouped into three ZIP archives according to the section
numbering of the revised manuscript.

## Contents

### [`Codes for section 4.zip`](Codes%20for%20section%204.zip)

This archive contains two programs supporting the computations in Section 4.
They perform the explicit calculations in the relevant cyclotomic fields,
including the integral-basis divisibility checks and the class-group
calculation used in the proof and in Appendix B. The class-group computation
in `section4_program2.txt` is certified using `bnfcertify`.

### [`Codes for the numerical experiments in section 5.zip`](Codes%20for%20the%20numerical%20experiments%20in%20section%205.zip)

This archive contains the three programs for the numerical experiments in
Section 5, Remark 10, corresponding to Cases (I), (II), and (III) of the
endpoint-extension theorem. The accompanying README specifies the sets being
counted, explains the treatment of the Wieferich prime 3511, and records the
results for the ranges used in the manuscript.

These computations are direct finite counts of explicit congruence,
Kronecker-symbol, multiplicative-order, and gcd conditions. They are
unconditional and should be distinguished from the density statements in the
manuscript that are conditional on GRH.

### [`Codes for section 6.zip`](Codes%20for%20section%206.zip)

This archive contains the programs and certificates supporting the
computational results in Section 6. It includes:

- the principal-ideal and support searches in the relevant descent fields;
- the certified quartic benchmark computation;
- separate checks for the two exceptional parameter triples;
- `section6_diophantine_solutions.pdf`, containing exact norm-form
  certificates for the remaining parameter triples; and
- `Readme.pdf`, containing a detailed file inventory, running instructions,
  parameter tables, and a reproducibility checklist.

The parameter family with $p_1\equiv7\pmod 8$ and
$p_2\equiv5\pmod 8$ is the family from Case (2) of Feng's Theorem 4.1; it is
treated in Section 6 but is not one of the three cases of the current
endpoint-extension theorem.

## Requirements and basic usage

A recent version of [PARI/GP](https://pari.math.u-bordeaux.fr/) is required.
PARI/GP 2.19.0 or later is recommended.
The certified computations reported in the manuscript were
re-verified with PARI/GP 2.19.0.
After downloading and extracting an archive, start GP in the corresponding
directory and load a program with `\r`. For example,

```text
\r type_3mod8_5mod8.txt
```

The Section 5 files define functions that should be called after the file is
loaded. For example,

```text
\r section5_caseI_numerical_experiment.txt
count_CaseI_pairs(200)
```

Use the bound `200000` to reproduce the full range reported in Remark 10.
For the Section 6 programs, the input parameters are collected near the
beginning of each file. Some of the large-field computations can require
substantial time and memory.

## GRH status of the Section 6 computations

The large-field endpoint programs use `bnfinit` without `bnfcertify`.
Consequently, the reported first principal-ideal endpoints and the resulting
nonexistence statements are conditional on GRH, as stated in the manuscript.

The program `determine_m.txt` calls `bnfcertify` and stops if certification
fails, so every quartic benchmark value reported by a completed run is
unconditional. The identities in `section6_diophantine_solutions.pdf` are
exact integer identities and are also unconditional. For the two exceptional
parameter triples, the corresponding programs recover generators with
`bnfisprincipal` and verify the final norm identities by exact arithmetic.
Nevertheless, the equality of the ideal and element endpoints remains
conditional on GRH because identifying the reported exponent as the first
principal-ideal endpoint uses the uncertified large-field class-group data.

For further details, see `Readme.pdf` inside `Codes for section 6.zip`.

## Associated manuscript

These files accompany a revised manuscript submitted to *Designs, Codes and
Cryptography*. The revised manuscript is not currently available as a public
preprint. If the article is published, this section will be updated with the
final title and bibliographic information.
