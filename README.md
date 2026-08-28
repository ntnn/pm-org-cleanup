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

release-managers are excluded to update release branches.

## rulesets/default-branch.json

Blocks deleting or force pushing to the default branch.
Requires PRs with a code owner review.

release-managers are not excluded.

## rulesets/tags.json

Same as branches but for tags.
