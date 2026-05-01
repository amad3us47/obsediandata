

**Full Recon on a Single Target**:

```shell
./reconftw.sh -d target.com -r
```

**Recon on Multiple Targets**:

```shell
./reconftw.sh -l targets.txt -r -o /path/to/output/
```

**Deep Recon (VPS Recommended)**:

```shell
./reconftw.sh -d target.com -r --deep
```

**Multi-Domain Recon**:

```shell
./reconftw.sh -m company -l domains.txt -r
```

**Axiom Integration**:

```shell
./reconftw.sh -d target.com -r -v
```

**Full Recon with Attacks (YOLO Mode)**:

```shell
./reconftw.sh -d target.com -a
```