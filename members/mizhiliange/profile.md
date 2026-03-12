# Daily Learning Log — 2026-03-12

**Author**: mizhiliange
**Date**: 2026-03-12

---

## What I Worked On Today

I used otel-demo to configure link collection, use telemetrygen to generate testing traces and load them to jaeger to conduct containerization and local evaluation.

---

## Key Insights

Traces attained in jaeger need to be labelized to suit for standard rcabench trace.parquet
OTel is responsible for instrumentation and export, while Jaeger is responsible for receiving, storing, and displaying traces. 

---

## What I Learned

The basic workflow of OpenTelemetry → Jaeger → trace data inspection.
Structural differences between Jaeger trace data and rcabench datapack format.
How to convert Jaeger-derived traces into a minimal rcabench-compatible dataset.
How to register and execute a custom algorithm in rcabench-platform v3 using the global algorithm registry.
How to run local evaluation with `./main.py eval single`.

---

## Errors and How I Resolved Them

### Error 1

**Description**:
`KeyError: 'my-algorithm'` occurred when running local evaluation.

**Steps taken**: 
Verified dataset structure and CLI arguments.
Inspected rcabench-platform v3 algorithm registry and execution flow.

**Resolution**: 
Registered the custom algorithm in `register_builtin_algorithms()` and ensured it was placed under `rcabench_platform/sdk/algorithms`.

---

### Error 2

**Description**:
`ModuleNotFoundError` caused by incorrect import paths (`v3/sdk/algorithms` vs `sdk/algorithms`).

**Steps taken**: 
Searched for the actual file location using `find` and `grep`.
Compared the project layout with rcabench-platform’s expected module structure.

**Resolution**:
Moved the algorithm implementation to `sdk/algorithms` and removed stale imports referencing non-existent paths.

---

### Error 3

**Description**: 
`ColumnNotFoundError` caused by schema mismatch of custom data and standard data.

**Steps taken**: 
Build a script to fix the coloum label.

**Resolution**:
Meet the minimum requirements of the official rcabench v3 for labels.parquet.

---

## Questions and Open Items

How should Jaeger trace attributes be normalized to better match rcabench benchmark schemas?

---

## Resources Referenced

OpenTelemetry Documentation
Jaeger Tracing Documentation
rcabench-platform v3 source code and CLI documentation

---

## Tomorrow's Plan

Learn Dataset Creator work
