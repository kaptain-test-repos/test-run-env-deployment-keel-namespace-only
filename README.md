# Test Run Env Deployment Keel Namespace Only

E2E test repo for the `kubernetes-run-environment` build in buildon-github-actions.

Tests deployMode `deployment` with imageAutoUpdateProvider `keel` under the
namespace-only permission model (`clusterScopedDelegation: parent`): the env's
cluster-scoped resources (from the vendor helm bundle) are split out of the
image-run manifest tree into the separate on-behalf dir for the RP parent to
apply. Also tests the mixed configuration source model (supplied checksum-named
Secret template in `src/environment`, generated ConfigMap) and
`expectedUndeclaredResources`.

Consumed as a child by `test-run-platform-cluster-scoped-on-behalf`.

Pending notes:

- Uses draft schema fields (`clusterScopedDelegation`) from the uncommitted
  `spec-kaptainpm-schema` repo; the schema must be faked into the build before
  this repo can build.
- The referenced reusable workflow does not exist yet; behaviour assertions
  (cluster-scoped split dir, checksum name enforcement) get added to the hooks
  once the reference scripts land.
