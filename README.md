# hecate-demo-fleet

The fleet repository for the [Hecate](https://github.com/olafkfreund/Hecate) demo.

**Every commit here was written by a machine.** Hecate clones this repo, repins an
image, commits, and pushes — one commit per promotion — and Flux applies the result
to the demo cluster. Nothing is edited by hand.

```
apps/dev/          what the dev namespace runs
apps/qa/           what the qa namespace runs
apps/production/   what the production namespace runs
```

The tag in each `kustomization.yaml` is the live one. To see a promotion, read the
commit history: each entry is one Bundle crossing one Gate.

A Bundle enters at dev and moves rightwards. dev and qa promote on their own; qa
admits only what cleared dev, and production only what cleared qa. Production
additionally requires a human approval, so a commit under `apps/production` means
someone said yes — not that someone had push access.

The pipeline that produces these commits is declared in
[`demo/pipeline.yaml`](https://github.com/olafkfreund/Hecate/blob/main/demo/pipeline.yaml).
