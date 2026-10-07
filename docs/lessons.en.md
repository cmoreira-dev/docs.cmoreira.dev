# Lessons learned

- **IaC boundaries must be disjoint.** Two controllers on the same state undo each other.
- **Safe defaults cost the consumer.** A generic chart with a restricted `securityContext` forces images to run
  non-root on an unprivileged port. Worth it, but it must be documented in the chart.
- **Coupled dependencies move together.** In ML/GPU stacks (runtime, CUDA, numeric libraries), upgrading one piece
  alone breaks the others. Group the updates and test the whole stack.
- **Not every repository has PR CI.** Where builds only run on merge, validate locally before merging.
- **Docs that live far from the code go stale.** Technical detail next to the repository; here only what is
  worth generalising.
