# Changelog (Unreleased)

Record image-affecting changes to `manager/`, `worker/`, `openclaw-base/` here before the next release.

---

- feat(hiclaw-controller): honor a new `spec.env` (`map[string]string`) field on Worker, Manager, Team.leader, and Team.workers[] CRs — user-declared variables are injected into the target container alongside the system-managed ones, with system-produced keys winning any collision (ignored user keys are logged at INFO level with the offending key list). Wired at `createMemberContainer` (covers standalone Workers and both Team roles via the existing `WorkerSpec` projection) and `createManagerContainer`; the `WorkerEnvBuilder` stays pure. CRDs add an `env` property block with `additionalProperties.type=string` and `propertyNames.pattern=^[a-zA-Z_][a-zA-Z0-9_]*$` so non-POSIX keys are rejected at admission. `hiclaw` CLI / REST API surface is intentionally deferred — users apply env via `kubectl apply -f` directly for now.
