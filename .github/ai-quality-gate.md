# AI quality gate

The organisation supplies the public AI quality gate centrally, so this
repository does not need a local caller workflow.

The check reads pull-request metadata, changed-file patches, reviews and review
threads through GitHub APIs. It does not check out or execute pull-request code,
and submitted text is treated as evidence rather than instructions.

An assessment records the exact pull-request head commit and the base repository,
branch and commit. Before publishing a verdict, the check verifies that the head,
base and review-feedback snapshot still match the evidence it assessed. Changed
or incomplete evidence fails closed rather than implying a passing result.

The AI gate does not impose a minimum number of human approvals. Missing human
approvals or pending CI alone do not prevent PASS; unresolved review threads,
current change requests and blocking findings prevent PASS. The repository's
other merge requirements still apply.
