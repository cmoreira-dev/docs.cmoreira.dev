---
description: "What broke or surprised while operating the platform."
---

# Lessons learned

- **IaC boundaries must be disjoint.** Two controllers on the same state undo each other.
- **Safe defaults cost the consumer.** A generic chart with a restricted `securityContext` forces images to run
  non-root on an unprivileged port. Worth it, but it must be documented in the chart.
- **Coupled dependencies move together.** In ML/GPU stacks (runtime, CUDA, numeric libraries), upgrading one piece
  alone breaks the others. Group the updates and test the whole stack.
- **Not every repository has PR CI.** Where builds only run on merge, validate locally before merging.
- **Docs that live far from the code go stale.** Technical detail next to the repository; here only what is
  worth generalizing.
- **A green CI does not prove anything was planned.** Terragrunt's git filter only sees changes to a unit's
  configuration file; a change only inside the local module or a lockfile gives an empty list and the pipeline passes
  having planned nothing. Find the unit from the changed file and fail loudly when an infra file belongs to no unit.
- **"Read-only" is not always read-only.** For Terraform to plan a Helm release, the identity must list Secrets in the
  namespace, and that includes the GitOps tool's own session keys. Whoever reads them is effectively admin. Instead of a
  "read-only" identity that does not exist, move that plan to the step that already has admin credentials.
- **Split by blast radius, not by repository.** What touches nodes or VMs needs a human step; the rest applies itself.
  And what the pipeline assumes (its own roles) cannot be managed by it: it stays in the manual bootstrap.
- **Adopting means proving zero differences.** When bringing existing resources under IaC, the first plan must say "no
  changes"; any difference is a stop. For generated OS configuration, the proof is the per-node hash of the output,
  identical to the previous one.
- **Small boards: 64-bit.** A CI runner on a 32-bit ARM board failed (TLS and the Node runtime). Reinstalling in
  64-bit cost less than working around it.
