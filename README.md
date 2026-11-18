# Hi, I'm LiRvs-Miria

I build compilers and debuggers for industrial control systems, with a
security background. My interests converge on one thread: **invariants** —
breaking them (security), guaranteeing them by construction (compilers),
refuting them automatically (program analysis), and eventually proving
them (machine-checked formal methods).

## Now

- [mlir-opt-fuzzer](https://github.com/LiRvs-Miria/mlir-opt-fuzzer) —
  in-tree fuzz target under review upstream
  ([PR #239171](https://github.com/llvm/llvm-project/pull/239171))
- [RFC] RemoveDeadValues: declared side effects vs derived liveness in
  dead functions
  ([discourse](https://discourse.llvm.org/t/rfc-removedeadvalues-declared-side-effects-vs-derived-liveness-in-dead-functions))
- [symrepl](https://github.com/LiRvs-Miria/symrepl) — replaying KLEE
  counterexamples under LLDB
- Day job: MLIR-based compiler for IEC 61499 / IEC 61131-3 (Structured
  Text) — custom dialects, lowering to LLVM IR, DAP debug stack

## Upstream record

Merged:

- [#226880](https://github.com/llvm/llvm-project/pull/226880)
  [lldb][Linux] false watchpoint stop on aarch64 single-step: the kernel
  reports single-step as TRAP_HWBKPT, so an uninitialized
  register-context out-param turned every step into a phantom hit
- [#243023](https://github.com/llvm/llvm-project/pull/243023)
  [mlir][WasmSSA] mark `wasmssa.return` as `ReturnLike`: without the
  trait, `-remove-dead-values` erased a function's dead results but left
  the terminator operands behind, leaving IR that no longer verified —
  found by the fuzzer (issue #242375)
- [#243322](https://github.com/llvm/llvm-project/pull/243322)
  [mlir][WasmSSA] add missing `MLIRControlFlowInterfaces` link
  dependency: `ReturnLike` implicitly requires
  `RegionBranchTerminatorOpInterface`, whose implementation lives in
  `MLIRControlFlowInterfaces`; verified with a local RED→GREEN
  shared-library build

Under review:

- [#227263](https://github.com/llvm/llvm-project/pull/227263)
  [mlir][tblgen] error on unsubstituted `$_self` in op trait predicates
- [#239171](https://github.com/llvm/llvm-project/pull/239171) [mlir] add
  an mlir-opt-fuzzer fuzz target (proposed and approved on
  [discourse](https://discourse.llvm.org/t/fuzzing-mlir-infrastructure/84855);
  reporting follows the
  [triager-aggregation model](https://discourse.llvm.org/t/fuzzing-mlir-infrastructure/84855/13)
  adopted in-thread)

Filed / repro / triage:

- [#242375](https://github.com/llvm/llvm-project/issues/242375),
  [#237126](https://github.com/llvm/llvm-project/issues/237126) —
  fuzzer-found MLIR crashes
- [#226008](https://github.com/llvm/llvm-project/issues/226008) —
  independent repro of the open SCCP dataflow crash via a different
  async construct; validating the fix
  ([#226086](https://github.com/llvm/llvm-project/pull/226086))
- [#184728](https://github.com/llvm/llvm-project/issues/184728) — lldb
  22.x debuginfod abort: `/bin/true` reproducer, verified workarounds
  ([Debian #1152537](https://bugs.debian.org/1152537)) — closed upstream

## Projects

- [mlir-opt-fuzzer](https://github.com/LiRvs-Miria/mlir-opt-fuzzer) —
  pass-pipeline fuzzer for MLIR: startup-selected pipelines from a closed
  `.def` vocabulary, verify-after-pipeline oracle, and a structural
  mutator (synonymous / missense / nonsense gene-level strategies, every
  candidate gated through parse + verify). First campaign: 7 crash
  classes, 2 in the valid-IR class; the follow-up campaign produced
  issue #242375, filed and fixed in-tree within four days. MLIR annex to
  the fuzzer-issue guidelines offered on the
  [RFC thread](https://discourse.llvm.org/t/rfc-guidelines-for-fuzzer-generated-issues/82556/8).
- [symrepl](https://github.com/LiRvs-Miria/symrepl) — replay KLEE
  symbolic-execution counterexamples under LLDB: path-condition-aware
  breakpoints, step-by-step input injection, state dumps. Debugger-side
  foundation for [dbgfuzz](https://github.com/LiRvs-Miria/dbgfuzz), a
  coverage-guided fuzzing platform.

## Background

- **Day job (closed source)** — an MLIR-based compiler for IEC 61499 /
  IEC 61131-3: custom MLIR dialects (TableGen ODS: ops, types,
  interfaces, constraints), a multi-stage lowering pipeline down to
  LLVM IR, and a DAP-based debug stack (`lldb-dap` / `lldb-server`) that
  debugs compiled artifacts on real aarch64 targets.
- **Security (5 years)** — binary reverse engineering, PKI/CA trust
  systems, WAF and vulnerability scanning, anti-tamper engineering
  (Linux anti-hook, hardware fingerprinting).
- **Compilers & debuggers** — MLIR / TableGen (ODS, DRR), lowering and
  rewrite pipelines, LLVM IR, DWARF, LLDB internals (`lldb-server`,
  ptrace, hardware debug registers), the DAP protocol and tooling.

## Toolbox

C/C++20 · MLIR / LLVM · TableGen · Python · CMake · Haskell

## Direction

Security and program analysis for the infrastructure that builds and
inspects programs — debug protocols, toolchains, and the IR layer:
measuring their attack surfaces, making protection strength measurable,
and closing the loop between symbolic execution and the debugger.
Formal methods stay on the horizon.
