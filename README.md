# Hi, I'm LiRvs-Miria

I build compilers and debuggers for industrial control systems, with a
security background. My interests converge on one thread: **invariants** —
breaking them (security), guaranteeing them by construction (compilers),
refuting them automatically (program analysis), and eventually proving
them (machine-checked formal methods).

## Now

- **LLVM upstream contributions**
  - Merged — `[lldb-server]` false watchpoint stop on aarch64 single-step:
    the kernel reports single-step as TRAP_HWBKPT, so an uninitialized
    register-context out-param turned every step into a phantom hit —
    [PR #226880](https://github.com/llvm/llvm-project/pull/226880)
  - In review — `[mlir][tblgen]` Error on unsubstituted `$_self` in op trait
    predicates — [PR #227263](https://github.com/llvm/llvm-project/pull/227263)
- **[symrepl](https://github.com/LiRvs-Miria/symrepl)** — replay KLEE
  symbolic-execution counterexamples under LLDB: path-condition-aware
  breakpoints, step-by-step input injection, state dumps. Debugger-side
  foundation for [ptrfuzz](https://github.com/LiRvs-Miria/ptrfuzz), a
  coverage-guided fuzzing platform.
- **Day job (closed source)** — an MLIR-based compiler for IEC 61499 /
  IEC 61131-3 (Structured Text): custom MLIR dialects (TableGen ODS: ops,
  types, interfaces, constraints), a multi-stage lowering pipeline down to
  LLVM IR, and a DAP-based debug stack (`lldb-dap` / `lldb-server`) that
  debugs compiled artifacts on real aarch64 targets.

## Background

- **Security (5 years)** — binary reverse engineering, PKI/CA trust
  systems, WAF and vulnerability scanning, anti-tamper engineering
  (Linux anti-hook, hardware fingerprinting).
- **Compilers & debuggers** — MLIR / TableGen (ODS, DRR), lowering and
  rewrite pipelines, LLVM IR, DWARF, LLDB internals (`lldb-server`,
  ptrace, hardware debug registers), the DAP protocol and tooling.

## Toolbox

C/C++20 · MLIR / LLVM · TableGen · Python · CMake

## Direction

Security and program analysis for the infrastructure that builds and
inspects programs — debug protocols, toolchains, and the IR layer:
measuring their attack surfaces, making protection strength measurable,
and closing the loop between symbolic execution and the debugger.
Formal methods stay on the horizon.
