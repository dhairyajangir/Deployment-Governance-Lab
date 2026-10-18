# Deployment governance audit

Baseline: no environments existed in this fork. The shipped workflow triggered
on every branch, omitted environment: production, requested id-token: write
without using OIDC, and printed database/token values into logs.

Controls applied: main-only push and job conditions; production environment;
one required reviewer (the owner of this personal training fork); a one-minute
wait timer; main-only deployment branch policy; administrator bypass disabled;
contents: read only; a ten-minute timeout; and no credential values in logs.

DEPLOY_KEY, DATABASE_URL and API_TOKEN are environment-scoped dummy lab values.
They grant no access to any outside system. No real production credentials were
copied or created. The release step only prints a simulation message.

This personal lab allows owner self-review so the owner can demonstrate the
approval flow alone. A shared production repository should use an independent
reviewer and prevent self-review. GitHub environment reviewers are an any-one
approval gate, not a promise that every listed reviewer must approve.

Behavioral validation: inspect the run waiting for the production environment,
then approve it and verify the build/test and simulated release finish.
