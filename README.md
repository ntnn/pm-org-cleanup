see <https://github.com/platform-mesh/backlog/issues/378>

# rulesets

## rulesets/branches.json

Blocks creating, updating, deleting and force pushing all branches
except the default branch. This is to prevent users with write
permissions that are not in the release-managers group from changing
branches.

The default branch is excluded because a PR merge counts as an update,
so no one but release-manager could merge PRs.

The default branch is guarded by the next rule.

repository admins are excluded - generally these shouldn't be set but
when setting up a repository there needs to be a way for a non-admin to
do the setup.

release-managers are excluded to update release branches.
bots like renovate and platform-mesh-publisher are excluded because they need to create and update branches to create PRs from.

## rulesets/default-branch.json

Blocks deleting or force pushing to the default branch.
Requires PRs with a code owner review, dismissed reviews etcpp

release-managers are not excluded.

repository admins are excluded - generally these shouldn't be set but
when setting up a repository there needs to be a way for a non-admin to
do the setup.

## rulesets/tags.json

Same as branches but for tags.
Here only platform-mesh-publisher is excluded because it creates tags for release candidates and builds.

repository admins are not exclude.

## rulesets/quality-gate.json

Requires the `quality-gate` job to pass on PRs in some repo types.
