# Hi, I'm LiRvs-Miria

Compiler engineer focused on MLIR-based compilers for industrial control.

## What I work on

- **MLIR compiler for IEC 61499 / IEC 61131-3 (Structured Text)** — custom MLIR dialects
  for function blocks, algorithms and ABI (TableGen ODS: ops, types, interfaces,
  constraints), with lowering pipelines that bring control programs down to LLVM IR.
- **TableGen / ODS / DRR** — op definitions, traits and constraints, DAG rewrite rules,
  and the `mlir-tblgen` code-generation workflows around them.
- **Compiler refactoring** — restructuring the lowering pipeline into small, independent,
  testable passes, from the ST frontend down to LLVM IR.
- **Toolchain debugging** — a DAP-based debug stack on `lldb-dap` / `lldb-server`
  that debugs the compiled artifacts on real aarch64 targets.

## Interests

MLIR - TableGen (ODS / DRR) - lowering & rewrite pipelines - LLVM IR - DWARF -
industrial control runtimes - embedded Linux (aarch64)

## Tools

C++ - CMake - MLIR / LLVM 20 - TableGen - ANTLR - Python - TypeScript - aarch64 embedded Linux
