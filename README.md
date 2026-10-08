# Hi, I'm LiRvs-Miria

I build compilers and debuggers for industrial control systems, with a
security background. My interests converge on one thread: **invariants** —
breaking them (security), guaranteeing them by construction (compilers),
refuting them automatically (program analysis), and eventually proving
them (machine-checked formal methods).

## Now

- **LLVM upstream contributions**
  - Merged — `[lldb-server]` Fix false watchpoint stop on single-step when the
    hardware debug regset read fails (aarch64) —
    [PR #226880](https://github.com/llvm/llvm-project/pull/226880)
  - In review — `[mlir][tblgen]` Error on unsubstituted `$_self` in op trait
    predicates — [PR #227263](https://github.com/llvm/llvm-project/pull/227263)
- **[symrepl](https://github.com/LiRvs-Miria/symrepl)** — replay KLEE
  symbolic-execution counterexamples under LLDB: path-condition-aware
  breakpoints, step-by-step input injection, state dumps.
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

C/C++20 · MLIR / LLVM · TableGen · Python · TypeScript · LLDB / DAP ·
ptrace · DWARF · aarch64 embedded Linux · CMake · ANTLR

## Direction

Program analysis on MLIR — dataflow and symbolic execution on custom
dialects — as the road toward formal methods: translation validation for
lowering pipelines, and machine-checkable guarantees for the languages
I build.
