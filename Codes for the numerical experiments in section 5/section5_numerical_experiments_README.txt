Numerical experiments for Section 5, Remark 10 (PARI/GP)

1. Scope

These three scripts reproduce the unconditional numerical experiments
mentioned in Remark 10 of Section 5.  They correspond, respectively, to
Cases (I), (II), and (III) of the endpoint-extension theorem.  The bound B
is applied to both prime variables p1 and p2.

The computations are direct finite counts of explicit congruence,
Kronecker-symbol, multiplicative-order, and gcd conditions.  They do not use
GRH.  This should be distinguished from the density statements in the
preceding remark of the manuscript, which are conditional on GRH.

2. Files and commands

  section5_caseI_numerical_experiment.txt     count_CaseI_pairs(B)
  section5_caseII_numerical_experiment.txt    count_CaseII_pairs(B)
  section5_caseIII_numerical_experiment.txt   count_CaseIII_pairs(B)

For example, load and run the Case (I) script in GP with

  \r section5_caseI_numerical_experiment.txt
  count_CaseI_pairs(200)

The argument 200 gives a quick test.  Use B = 200000 to reproduce the full
range reported in the manuscript.

3. Sets counted by the programs

Case (I)

  Base set:
    p1 == 3 (mod 8), p2 == 5 (mod 8), and kronecker(p1,p2) == -1.

  Order set:
    the subset of the base set for which
    ord_(p1*p2)(2) = eulerphi(p1*p2)/2.

Case (II)

  Base set:
    p1 == 7 (mod 8), p2 == 1 (mod 8), kronecker(p1,p2) == -1,
    and p1 != 3511.

  Order set:
    the subset of the base set for which
    ord_p1(2) = (p1-1)/2,
    ord_p2(2) = (p2-1)/2, and
    gcd((p1-1)/2,p2-1) = 1.

  Non-quartic comparison set:
    the subset of the base set for which 2 is not a quartic residue
    modulo p2.

Case (III)

  Base set:
    p1 == 3 (mod 8), p2 == 1 (mod 8), and kronecker(p1,p2) == -1.

  Order set:
    the subset of the base set for which
    ord_p1(2) = p1-1,
    ord_p2(2) = (p2-1)/2, and
    gcd((p1-1)/2,p2-1) = 1.

  Non-quartic comparison set:
    the subset of the base set for which 2 is not a quartic residue
    modulo p2.

In Cases (II) and (III), ord_p2(2) = (p2-1)/2 implies that 2 is not a
quartic residue modulo p2.  Hence the order set is contained in the
non-quartic comparison set.

4. Why p1 = 3511 is excluded in Case (II)

A base-2 Wieferich prime is a prime p satisfying

  2^(p-1) == 1 (mod p^2).

The local formulation of the maximal-order condition in Section 5 uses the
prime-power lifting formula

  ord_(p^e)(2) = p^(e-1)*ord_p(2),

which is applied under the assumption that p is not a base-2 Wieferich
prime.  In the range of these experiments, the only base-2 Wieferich primes
are 1093 and 3511.  Their relevant properties are

  1093 == 5 (mod 8),  ord_1093(2) = 364 != 1092;
  3511 == 7 (mod 8),  ord_3511(2) = 1755 = (3511-1)/2.

For the Wieferich-prime search result, see F. G. Dorais and D. Klyve,
"A Wieferich Prime Search up to 6.7 x 10^15," Journal of Integer
Sequences 14 (2011), Article 11.9.2.

Thus 1093 does not pass the Case (I) maximal-order test, whereas 3511 would
otherwise pass the prime-level order test for p1 in Case (II), despite not
satisfying the lifting hypothesis.  The Case (II) program therefore excludes
p1 = 3511 explicitly.  The congruence and order conditions already prevent
1093 and 3511 from causing the same issue in the other cases, so no further
explicit exclusion is needed.

5. Purpose of the non-quartic comparison set

The non-quartic-residue hypothesis was used in the earlier Feng--Liu results
for the parameter families underlying Cases (II) and (III).  The current
endpoint theorem uses the stronger multiplicative-order condition.  The
programs retain the non-quartic set only as a benchmark, so that the frequency
of the current order condition can be compared with that of the earlier
hypothesis.  It is not an additional condition imposed by the programs on the
order set.

The ratios printed by the Case (II) and Case (III) programs are

  R1 = (size of order set)/(size of base set),
  R2 = (size of order set)/(size of non-quartic comparison set).

For a fixed admissible p1, the non-quartic comparison set has asymptotically
half the density of the base set in the p2-variable.  This explains why the
observed value of R2 is approximately twice that of R1.  This density
interpretation is not used in the finite computations.

6. Numerical results

Case (I)

  B          Base set     Order set       R1
  200              84            51     0.6071428571
  2000           3061          1280     0.4181639987
  20000        163755         66604     0.4067295655
  200000     10159306       4280683     0.4213558485

Case (II)

  B          Base set     Order set     Non-quartic set       R1             R2
  200              58            22                    34     0.3793103448   0.6470588235
  2000           2767           619                  1383     0.2237079870   0.4475777296
  20000        158891         35493                 82418     0.2233795495   0.4306462181
  200000     10108964       2169524               5091168     0.2146138813   0.4261348280

Case (III)

  B          Base set     Order set     Non-quartic set       R1             R2
  200              51            22                    29     0.4313725490   0.7586206897
  2000           2681           553                  1330     0.2062663185   0.4157894737
  20000        159842         35333                 82741     0.2210495364   0.4270313388
  200000     10055849       2149134               5064762     0.2137197963   0.4243306991
