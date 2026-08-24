# hecate-demo-fleet

The fleet repository for the [Hecate](https://github.com/olafkfreund/Hecate) demo.

**Every commit here was written by a machine.** Hecate clones this repo, repins an
image, commits, and pushes — one commit per promotion — and Flux applies the result
to the demo cluster. Nothing is edited by hand.

```
apps/staging/      what the staging namespace runs
apps/production/   what the production namespace runs
```

The tag in each `kustomization.yaml` is the live one. To see a promotion, read the
commit history: each entry is one Bundle crossing one Gate.

Staging promotes automatically. Production requires a human approval *and* a
compliance check against evidence — so a commit landing in `apps/production` means
something passed a gate, not that someone had push access.
